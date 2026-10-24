# instabox-mcp

A small stdio MCP server for [InstaBox](https://instabox.sh/) that exposes
Linux cloud machines to an MCP client (e.g. OpenCode) without installing the
InstaBox CLI.

## Features

- List/get/create/delete machines
- Run commands (`instabox_exec`) with `cwd`, `envs`, `stdin`, timeout
- Read files/directories and write files
- `instabox_ensure_machine`: get-or-create convenience helper
- Auto-polls create/delete operations until done
- Resolves machine names to IDs (file endpoints need IDs)
- Credentials loaded once from `~/.config/instabox/env`

## Install

```sh
git clone git@github.com:twili8/instabox-mcp.git
cd instabox-mcp
chmod +x instabox-mcp
ln -s "$PWD/instabox-mcp" ~/.local/bin/instabox-mcp
```

Create `~/.config/instabox/env`:

```sh
INSTABOX_API_KEY=ibk_...
INSTABOX_API_URL=https://api.instabox.sh
chmod 600 ~/.config/instabox/env
```

## OpenCode config

Add to `~/.config/opencode/opencode.jsonc`:

```jsonc
{
  "mcp": {
    "instabox": {
      "type": "local",
      "command": ["/home/dev/.local/bin/instabox-mcp"],
      "enabled": true
    }
  }
}
```

## Tools

- `instabox_me`
- `instabox_usage`
- `instabox_templates`
- `instabox_list_machines`
- `instabox_get_machine`
- `instabox_create_machine`
- `instabox_delete_machine`
- `instabox_exec`
- `instabox_read_file`
- `instabox_write_file`
- `instabox_ensure_machine`
- `instabox_start_machine`
- `instabox_stop_machine`
- `instabox_suspend_machine`
- `instabox_resume_machine`
- `instabox_update_machine`

## Initialize credentials

CLI:

```sh
ibx init --key ibk_... --url https://api.instabox.sh
```

MCP tool: `instabox_init` with `apiKey` (and optional `apiUrl`).
PY


The API key is stored locally with mode 600 and never committed. Only the
MCP server script and this README belong in the repo.
PY
