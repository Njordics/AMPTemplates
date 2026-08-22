# Njordics AMP Templates

Community-maintained [CubeCoders AMP](https://cubecoders.com/AMP) deployment templates.

## Active Templates

Templates in this section are fully active and ready to deploy.

| Template | Status | Notes |
| --- | --- | --- |
| MotorTown | Working | Windows dedicated server running through Wine. Ignore the "X connection to :99" broken message; it is a harmless Wine/Steam startup check and can be safely ignored. |

## In Development

Templates in this section are works in progress and may require further testing or configuration changes.

| Template | Status | Notes |
| --- | --- | --- |
| Schedule I | Needs testing | Windows dedicated server powered by the open-source [S1DedicatedServers / DedicatedServerMod](https://github.com/ifBars/S1DedicatedServers) (GPL-3.0). Fully automated update (SteamCMD + GitHub Releases) and fully configurable, but unverified against a real deployment (executable name, TOML config mapping, and console behavior are all best-effort). See notes below.

### Schedule I notes

- Requires a Steam account that owns Schedule I (SteamCMD login, not anonymous).
- Every **Update** downloads the game via SteamCMD and fetches the matching `S1DedicatedServers` release build directly from GitHub Releases (`ifBars/S1DedicatedServers`) - no manual downloads or third-party site logins are needed, unlike the Nexus-hosted alternative mod.
- The **Server Runtime** setting (Configuration tab) picks IL2CPP (default Schedule I branch) or Mono (`alternate` branch) - pick one and run an Update before first start.
- Most settings (name, password, player limit, authentication, messaging backend, TCP console, performance, debug) are applied via command-line overrides, which take precedence over the config file.
- Save path, auto-save, and gameplay/time settings have no CLI override and are instead written directly into `UserData/server_config.toml`. AMP officially only guarantees `ini`/`kvp`/`json` config parsing, so mapping onto this TOML file is best-effort - verify the file's contents after saving Configuration changes.
- Operators/permissions are managed via `permissions.toml` and console commands (`op <steamid>`, `admin <steamid>`, `perm grant ...`) rather than a config field - see the [Permissions docs](https://docs.s1servers.com/docs/configuration/permissions.html).
- The console understands `save`, `serverinfo`, `listplayers`, `settime`, and the graceful stop command is `shutdown` (wired to AMP's Stop button).
- Full docs: https://docs.s1servers.com/

## Issue Requests and Bug Reports

If you want to request a new game template, or if you find a bug in an existing template, open an issue using the format `[Game Request]` and/or `[Bug Found]` in the issue title so it can be triaged correctly.

## Adding This Repository to AMP

1. In AMP, open `Configuration` then `Instance Deployment`.
2. Add `Njordics/AMPTemplates:main` as a Configuration Repository.
3. Fetch the repository, refresh AMP, and select the desired template when creating an instance.
