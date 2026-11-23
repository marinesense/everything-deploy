# everything-deploy

Coolify deployment of selected apps from [HeyPuter/everything](https://github.com/HeyPuter/everything).
Each app is built from upstream `main` at image build time (`UPSTREAM_REF` build arg) and served by nginx.
Update: redeploy with force in Coolify. Add an app: copy a service block in `deploy/coolify/compose.yaml`.
Frontends only; storage and auth still use Puter's cloud.
