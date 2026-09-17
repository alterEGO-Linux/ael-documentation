<!--
=============================================================================== 
INFO
===============================================================================
 [/ael-documentation/components/ael-bar/widgets/ael-pip.md]

 Author      : Pascal Malouin (https://github.com/alterEGO-Linux)
 Created     : 2026-09-16 21:29:09 UTC
 Updated     : 2026-09-16 21:29:09 UTC
 Description : AEL//PiP
-------------------------------------------------------------------------------
-->

# AEL//PiP

## Dev

```bash
hyprctl clients -j | jq '.[] | {
    class,
    initialClass,
    title,
    initialTitle,
    xwayland,
    floating,
    fullscreen
}'

[...]
{
  "class": "zen",
  "initialClass": "zen",
  "title": "Picture-in-Picture",
  "initialTitle": "Picture-in-Picture",
  "xwayland": false,
  "floating": true,
  "fullscreen": 0
}
```
