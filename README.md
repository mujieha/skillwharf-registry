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

The `source` must be a public GitHub source (`github:owner/repo[/path]`).
skillwharf drops entries that are not.

## License

The index is MIT licensed. The skills it points at carry their own licenses.
