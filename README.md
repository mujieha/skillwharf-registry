# skillwharf-registry

The default registry for [skillwharf](https://github.com/mujieha/skillwharf): one
`index.json` that `skillwharf search` reads when no `--registry` is given.

```
skillwharf search pdf
skillwharf add github:anthropics/skills/skills/pdf
```

Each entry points at a skill that lives in its own repository. Nothing is copied
here, and each skill keeps the license in its own folder upstream.

## Adding a skill

Open a pull request against `develop` that adds one entry to `index.json`. The
easiest way is `skillwharf publish`:

```
skillwharf publish ./my-skill --registry ./skillwharf-registry --source github:you/skills/my-skill
```

This public index takes public GitHub sources only (`github:owner/repo//path`),
so anyone can read what an entry points at. That is a rule of this index, not of
skillwharf: your own registry can list skills on any git host.

## Your own registry

A team or company can run a registry next to this one, on its own git server:
a repository with one `index.json` in the same shape as this one. Its entries
may point at GitLab, Bitbucket, a self-hosted server or any git URL:

```json
{
  "version": 1,
  "skills": [
    { "name": "release-notes", "description": "Write release notes our way", "source": "gitlab:acme/platform/skills//release-notes" }
  ]
}
```

Add it to a project with
`skillwharf registry add acme git+ssh://git@git.acme.com/platform/skill-registry.git`,
commit `skillwharf.json`, and teammates get it with `skillwharf sync`. Searches
then cover both registries. `skillwharf registry help` explains it offline, and
the [guide](https://github.com/mujieha/skillwharf#your-own-registry) has the details.

## License

The index is MIT licensed. The skills it points at carry their own licenses.
