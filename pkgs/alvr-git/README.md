# ALVR

This package builds ALVR from upstream's development branch. Use a compatible development client on the headset.

## USB connections

The package bundles Android tools with a static wrapper that clears `LD_LIBRARY_PATH` before starting ADB. SteamVR supplies its own library paths, which can load libraries incompatible with ADB's dependencies.

Native USB setup selects this wrapper directly. Upstream's usual ADB lookup prefers the host's `PATH`, which can bypass the wrapper and leave ALVR disconnected even when ADB detects the headset from a terminal. Keep the native USB selection and wrapper isolation when updating the package.

The patch applies only to native USB setup. The ALVR launcher's handling of downloaded releases keeps upstream's ADB selection and download behavior.
