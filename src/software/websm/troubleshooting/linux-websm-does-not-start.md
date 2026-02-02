# [Vincent OS | Linux] WebSM does not start
```admonish info
Difficulty level: ⭐
```

This issue can happen if you are using a Wayland session, WebSM is build with Uno Platformn, which currently, have issues supporting Wayland sessions due to WebView2 limitations.

```admonish tip
The Flatpak version of WebSM is configured to use the X11 backend, so using the Flatpak version of WebSM can be a workaround for this issue.
```

To launch WebSM on X11 backend, add the following environment variable:

```bash
GDK_BACKEND=x11 websm
# Or if you are using the Lite version
GDK_BACKEND=x11 websm-lite
```

This will force WebSM to use the X11 backend, and should allow it to start correctly.