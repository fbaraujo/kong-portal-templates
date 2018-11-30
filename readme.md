# Kong Developer Portal Templates

Developer Portal Template Files for Kong Enterprise Edition

## Libraries Used

- [Handlebars](https://handlebarsjs.com/)
- [Swagger UI](https://github.com/swagger-api/swagger-ui)
- [VueJS](https://vuejs.org/)

## Installation

Install `npm` and `node`

```bash
$ git clone git@github.com:Kong/kong-portal-templates.git
$ npm install
```

## Directory Structure
- `templates/` - Developer Portal Theme files
  - `pages/` - Handlebars pages served by the dev portal
  - `partials/` - Handlebars partials, referenced by pages
  - `specs/` - Directory of OAS specifications for use by portal
  - `sync.js` - Script to create, and update theme files in the Kong File API

## Environment Variables

|Variable|Default|Description|
|---|---|---|
|`KA_API_URL`|`localhost:8004`|Kong Admin API URL|
|`KA_API_KEY`|`abcdef`|Sets `apikey` header on file requests|
|`KA_BASIC_AUTH`|`username:password`|Sets `Authorization` header on file requests|
|`KA_RBAC_TOKEN`|`abcdef`|Sets `kong-admin-token` header on file requests|
|`WORKSPACE`|`default`|Workspace in which to sync files with (`WORKSPACE=default` will sync files with `ADMIN_API_URL/workspaces/default/files`)
|`DIRECTORY`|`src/templates/`|Directory the sync script will scan and watch for changes.|
|`WATCH`|`true`|watch files for changes and sync with files api when a change is made.|
|`PUSH`|`true`|push files to Files API (compare to `git push --force`)|
|`PULL`|`true`|pull files from Files API (compare to `git pull`)|
|`DELETE_ALL`|`true`|`remove all files from Files API. USE WITH CAUTION!!!`|
|`INTERVAL`|`5`|Sync script watch interval in seconds|
|`TYPE`|Type of files the sync script is scanning. By default, the files are assumed to be directory based. `<type>/<filename>`|
|`EMOJI`|`false`|`true` enables emoji status symbol output in the sync script.|

### Example Usage

Watch Template files and sync on change
```bash
$ node sync
```

Sync files with a specific workspaces dev portal
```bash
$ WORKSPACE=custom_workpsace node sync
```

Push/Pull to Kong Files API
```bash
$ PUSH=true node sync
$ PULL=true node sync
```

Use Emoji's:
```bash
$ EMOJI=true node sync
```