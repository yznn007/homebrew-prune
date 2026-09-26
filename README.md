[English](README.md) | [简体中文](README.zh-CN.md)

# Homebrew Prune

When you manually delete an app from your Mac, Homebrew may keep its Cask record. A later `brew upgrade` can then report that the `.app` is missing.

This tap has one small cleanup script for those stale Cask records. It lists the candidates first and waits for your confirmation before asking Homebrew to uninstall them. One script, one cleanup command:

```sh
brew prune
```

## Quick start

Add the tap and trust its `prune` command:

```sh
brew tap yznn007/prune
brew trust --command yznn007/prune/prune
```

The trust command applies only to `prune` in this tap.

Then run:

```sh
brew prune
```

The script lists installed Casks whose declared app paths are all missing. Review the names and paths before confirming. Type `y` or `yes` to continue; press Return to cancel.

After confirmation, the script runs `brew uninstall --cask --force` for each listed Cask. Homebrew may also run actions defined by that Cask's uninstall stanza. The script does not use `--zap`.

## Caution

An app moved to another folder or an unmounted external drive may appear to be missing. Check the candidate list before confirming.

## Requirements

macOS, Homebrew, and Python 3.9 or newer. No additional Python packages are required.

## License

This project is licensed under the [MIT License](LICENSE).
