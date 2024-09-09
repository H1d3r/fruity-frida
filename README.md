# fruity-frida

Utils for deploying frida to rootless iOS and more

I took down the package from npm because it's not very much useful now as Sep 2024

## Commands

* `ios-shell` open a shell to iOS using default credentials (root/alpine). iproxy is automatically included so you don't need extra steps.
* `ios-debug` debug process or apps on jailbroken iOS. Automatically deploy debugserver, do the port forwarding and connect to it.
* `ios-pull` pull files and directories from iOS
* `iproxy-js` iproxy written in js
* `run-frida-server` automatically download, deploy frida-server to iOS and start it. Supports checkm8 based rootless environments.
* `get-ios-gadget` download gadget-ios.dylib from GitHub

### ios-debug

* `ios-debug attach <process name or pid>` attach to running process
* `ios-debug app <app name or bundle id>` spawn or attach to app by name or bundle id
* `ios-debug apps` list all apps

## Common Command Line Flags

By default, all the scripts choose one of your iDevices connected to USB. These frida options are supported.

```
-U, --usb            connect to USB device
-R, --remote         connect to remote frida-server
-D, --device <uuid>  connect to device with the given ID, useful when you have multiple devices
-H, --host <host>    connect to remote frida-server on HOST
-h, --help           display help for command
```

## SSH Environment Variables

The default credentials for ssh is `mobile` / `alpine`. 
You can change them by setting environment variables:

`SSH_PRIVATE_KEY`, `SSH_PASSPHRASE`, `SSH_PORT`, `SSH_USERNAME`, `SSH_PASSWORD`.

However, I can't guarantee they will work, since the lockdown (a protocol to talk to your devices, just like libimobiledevices)
functions from [frida-node](https://github.com/frida/frida-node) seems to only support USB connections.
