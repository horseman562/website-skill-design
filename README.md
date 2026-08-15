# Bayuratech Claude Code skills

Naqiuddin's own Claude Code plugin. Ships two skills:

**`pitch-site`** — build a spec-demo pitch site for a Malaysian SME prospect: research the
business from its social presence with Playwright, build a single-file HTML demo with a
design that's never been reused, and write the research + outreach docs.

**`dashboard-site`** — build a single-page analytics dashboard: KPI row, interactive charts
with crosshair tooltips, one filter row, and a table view, as a self-contained HTML file.
Ships a complete working dashboard as its reference implementation, and a colour palette
that is validated by script rather than chosen by eye.

---

## Install on a new laptop

Two commands, typed **inside Claude Code** (not in a terminal):

```
/plugin marketplace add horseman562/website-skill-design
/plugin install bayuratech-pitch@bayuratech
```

The first registers this repo as a marketplace named `bayuratech`. The second installs
the `bayuratech-pitch` plugin from it, which carries the `pitch-site` skill.

Restart Claude Code, then check it's there:

```
/plugin
```

`pitch-site` should be listed. Now just describe the job and the skill loads itself:

> build a pitch site for https://www.instagram.com/someshop/

Or invoke it by name with `/pitch-site`.

### Updating after you push changes

```
/plugin marketplace update bayuratech
```

### Alternative — no plugin system

Copy the skill straight into your personal skills folder:

```bash
git clone https://github.com/horseman562/website-skill-design.git /tmp/wsd
cp -r /tmp/wsd/skills/pitch-site ~/.claude/skills/pitch-site
```

The plugin route is preferred — one `/plugin marketplace update` keeps every machine in sync.

---

## Layout

```
.claude-plugin/
  marketplace.json          # makes the repo installable as a marketplace
  plugin.json               # plugin manifest
skills/
  pitch-site/
    SKILL.md                # the workflow
    reference/
      differentiation.md    # running table of every site's theme/hero/fonts
      architecture.md       # the house style
      page-skeleton.html    # token-driven boilerplate
      notes-template.md
      contacts-template.md
  dashboard-site/
    SKILL.md                # dashboard rules: form → colour → marks → interaction
    reference/
      dashboard-reference.html   # complete working dashboard
```

---

## ⚠️ Keep `differentiation.md` current

The one rule that makes this work: **no site may reuse a font pair, colour theme, or hero
layout.** After every build, append the new row to
`skills/pitch-site/reference/differentiation.md` and push. If that file goes stale, sites
start looking alike and the pitch loses its edge.
