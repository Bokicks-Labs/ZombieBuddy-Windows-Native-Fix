# ZombieBuddy Windows native loader fix

This repository hosts one patched `zbNative.dll` for ZombieBuddy 2.3.3 on
Windows, tested with Project Zomboid 42.21. It contains **no Project Zomboid
modpack source, artwork, saves, configuration, or Project Viewpoint files**.

The upstream loader uses an unqualified `LoadLibraryA("instrument.dll")` call.
The patched loader resolves `jre64\bin\instrument.dll` in the game directory
and loads it by full path. This avoids loading a second copy of the JRE's
`java.dll` and `instrument.dll` from the game root. It does not alter the Java
agent JAR or automatically install anything.

Release asset `zbNative.dll` SHA-256:

`49E5D596B54E5E4EAB535E613CDC7C3F0DE9BB7EF07239C255E2B127657104CE`

The DLL was tested on one Windows client: hostname connection succeeded and
Project Viewpoint ran, with only bundled-JRE Java DLLs mapped. Other machines
and future game versions need separate validation. Back up the original DLL
before installing and close the game first. The private Chaosworld setup helper
handles the download, checksum check, backup, and restore for its players.

ZombieBuddy is by Andrey "Zed" Zaikin. This is an unofficial modification,
not endorsed by ZombieBuddy, Project Viewpoint, or The Indie Stone. The binary
is distributed under ZombieBuddy's MIT license in [LICENSE](LICENSE). The
original project is at <https://github.com/zed-0xff/ZombieBuddy>.
