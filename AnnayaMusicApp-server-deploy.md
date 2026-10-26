# Deploy the Annaya Music server on Render

This project includes a Render Blueprint at the repository root. It builds the included Docker server, publishes an HTTPS web service, creates a 25 GB persistent disk at `/data`, generates the token-signing secret, and asks you to set the admin password during setup. The disk-backed plan is paid; Render does not keep uploaded files on its free ephemeral filesystem.

## First deployment

1. Unzip the project and put the **contents** into a new GitHub repository. Keep `render.yaml` at the repository root and the server files under `server/`.
2. Sign in to Render and choose **New + → Blueprint**. Connect the repository and select its default branch.
3. Review the `annaya-music-api` service. When prompted for `ADMIN_PASSWORD`, enter a strong password. The starter app's requested password is configured for local development; change it before publishing the service.
4. Confirm the paid compute plan and 25 GB disk, then create the Blueprint. Render will build the Docker image and deploy it. Persistent disks preserve uploaded songs and the catalog across restarts; they require a paid web service.
5. When the service is live, open its HTTPS address plus `/health`. A healthy response contains `"ok":true`.
6. In the app, open **Online**, enter the service's HTTPS origin (the part before `/health`), and refresh the shared catalog. In **Admin**, sign in with username `admin` and the password you set, then upload MP3/AAC files.

The Render address is created during deployment, so it cannot be prefilled in the APK. Enter it once in the app; it is saved on that phone. Other listeners enter the same HTTPS address.

## Existing local Docker option

To run the server yourself, use `server/README.md` and `server/compose.yaml`. The Render and local Docker setups both write persistent data under `/data`.

## Notes

- Keep the `ADMIN_PASSWORD` and generated `TOKEN_SECRET` private. Do not commit `.env` files or real songs to the repository.
- A persistent disk is single-instance storage. This Blueprint uses one server instance, which is appropriate for this file-backed starter server.
- The server starts with no songs. Upload only audio you have the right to distribute.
