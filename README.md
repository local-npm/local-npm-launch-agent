local-npm-launch-agent
====

Script to set up [local-npm](https://github.com/nolanlawson/local-npm/) as a LaunchAgent on OS X, so that you can get up and running with `local-npm` in no time.

Usage
---

Run this command (**without sudo!**):

    curl -sL https://raw.githubusercontent.com/nolanlawson/local-npm-launch-agent/master/local-npm-launch-agent.py | python -

### What this does

1. Installs `local-npm`, `pm2`, and `npmrc` globally.
2. Creates a LaunchAgent to run `pm2` and `local-npm`.
3. Creates an `npmrc` called `local` that points to local-npm.
4. Starts it up.

When you restart your machine, `local-npm` will already be up and running.

To see the output logs, you can run:

    pm2 logs all

To switch back to regular npm, you can run:

    npmrc default

You can also visit [http://localhost:5080/_browse](http://localhost:5080/_browse) in a browser to confirm that `local-npm` is up and running.

Uninstall
----

If at any point you want to uninstall all this stuff, just do:

    launchctl unload ~/Library/LaunchAgents/com.nolanlawson.localnpm.plist
    rm -fr ~/.local-npm ~/.npmrcs/local ~/Library/LaunchAgents/com.nolanlawson.localnpm.plist
    npmrc default