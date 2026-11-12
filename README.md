# EVSC Claude plugins

District plugins for EVSC's Claude Desktop deployment (Google Cloud Vertex AI).
Claude Desktop reads this repository as a plugin marketplace named
`evsc-staff`.

| Plugin | Skills | Who gets it |
| --- | --- | --- |
| `evsc-staff-essentials` | `copy-ready-text`, `pii-safe-writing` | All staff (installed automatically) |

- **copy-ready-text:** puts text that staff will paste somewhere else (emails,
  messages, form fields) in a block with a one-click copy button.
- **pii-safe-writing:** keeps names, student information and other personal
  details out of anything that will be saved, published or shared.

The skills are instructions only. They contain no connectors, hooks or code,
so nothing in this repository sends data anywhere or runs on a device.

## Layout

```
evsc-claude-plugins/
├── README.md
├── .claude-plugin/marketplace.json
└── plugins/evsc-staff-essentials/
    ├── .claude-plugin/plugin.json
    └── skills/
        ├── copy-ready-text/SKILL.md
        └── pii-safe-writing/SKILL.md
```

Keep every plugin inside this repository. Claude Desktop does not fetch
plugins whose `source` points at another repository, or git submodules.

## Requirements

- **Public repository:** devices read it without signing in
  (`credentialKind` `anonymous`). The files hold no names, IDs or secrets.
  Check that every change keeps it that way.
- **Git on every device:** Macs get it from the Xcode Command Line Tools
  (`xcode-select --install`). Windows devices need Git for Windows.
- **Network:** the app fetches the marketplace itself, outside Claude's
  sandbox, so `github.com` does not need to be in `coworkEgressAllowedHosts`.
  It does need to be reachable through the district network.

## Add it to the profiles

Copy the full 40-character SHA of the commit you want to deploy. Automatic
installation refuses branch and tag names. Then add this entry to
`allowedPluginMarketplaces` in both the staff and IT profiles, next to the
Anthropic marketplaces already there:

```json
{"source":"github","repo":"evscschools/evsc-claude-plugins","ref":"FULL_40_CHARACTER_COMMIT_SHA","credentialKind":"anonymous","installationPreference":"auto_install","expectedName":"evsc-staff"}
```

If the repository has a different name, change `repo` to match.

`auto_install` installs the plugin the first time a device sees the pinned
commit; users can still uninstall it. Use `required` instead to keep it
installed. `available` only lists it under
**Customize > Plugins > Discover > Organization**.

The in-app configuration window (**Plugins > Add marketplace > GitHub repo**)
builds and checks the same entry.

## Change a skill

1. Edit or add `plugins/evsc-staff-essentials/skills/<skill-name>/SKILL.md`.
2. Raise `version` in `plugins/evsc-staff-essentials/.claude-plugin/plugin.json`.
3. Commit and push, and copy the new commit SHA.
4. Update `ref` in both profiles and redeploy them. Devices pick up the new
   commit at the next launch or sync.

## Notes

- Anyone who already has one of these skills installed personally will see
  it twice. Remove the personal copy under **Settings > Skills** after the
  plugin installs.
- To remove the marketplace, delete its entry from the profiles. Devices
  uninstall its plugins at the next sync.
