# bbd-admin-fe

React + TypeScript frontend for the BBD admin console.

This app is intentionally separate from `bbd-admin-be`. It does not talk to Keycloak Admin REST and it does not keep any admin client secret. Login and provisioning APIs are delegated to the backend.

## Local Run

```powershell
Copy-Item .env.example .env
npm install
npm run dev
```

Default frontend URL:

```text
http://localhost:5174
```

Default backend URL:

```text
VITE_BBD_ADMIN_API_BASE=http://localhost:8090
```

## Login Flow

The login button sends the browser to:

```text
{VITE_BBD_ADMIN_API_BASE}/oauth2/authorization/keycloak
```

Spring Security handles the Keycloak authorization code flow in `bbd-admin-be`, then redirects back to this app. After that, this app calls backend APIs with `credentials: "include"` so the session cookie is sent.

## Build

```powershell
npm run build
```
