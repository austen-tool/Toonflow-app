# Building ToonFlow Application

## Toolchain

- Node.js `24.18.0`
- Yarn Classic `1.22.22`
- Windows x64 for the Electron installer

Use a Node version manager with `.nvmrc`, or install the exact Node.js release.
Corepack included with Node 24 can run the pinned Yarn version:

```powershell
corepack yarn --version
corepack yarn install --frozen-lockfile
```

Do not regenerate `yarn.lock` during a baseline build.

## Checks and Build

Run from the repository root:

```powershell
corepack yarn lint
corepack yarn build
corepack yarn dist:win:unsigned
```

The upstream repository does not currently define an automated test script.
`lint` performs the TypeScript no-emit check. `build` produces the backend
service and Electron main-process bundles. `dist:win:unsigned` creates the
unsigned Windows installer and unpacked Electron application under `dist/`.

The unsigned baseline sets electron-builder's
`win.signAndEditExecutable=false`. This avoids certificates and Windows
symbolic-link privileges, but it also disables executable icon, metadata and
execution-level editing. Use the normal signed release workflow only after
release signing and Windows build-agent privileges are configured.

## Local Smoke Test

After a successful build, start the compiled backend with:

```powershell
corepack yarn start
```

The service must remain running without an immediate uncaught exception and
respond on its configured local HTTP port. Stop it after the smoke test.

Run this backend smoke test before Electron packaging. electron-builder rebuilds
native modules for Electron's ABI; use a frozen forced install to restore the
Node.js ABI before running the standalone backend again:

```powershell
corepack yarn install --frozen-lockfile --force
```
