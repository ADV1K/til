# Remap caps lock

## make keyd an internal keyboard
`/etc/libinput/local-overrides.quirks`

```
[keyd virtual keyboard]
MatchName=keyd virtual keyboard
MatchUdevType=keyboard
MatchBus=usb
AttrKeyboardIntegration=internal

[keyd virtual pointer]
MatchName=keyd virtual pointer
MatchUdevType=mouse
MatchBus=usb
AttrKeyboardIntegration=internal
```

## keyd conf
`/etc/keyd/default.conf`

```
[ids]

*

[main]

# Maps capslock to escape when pressed and control when held.
capslock = overload(control, esc)
#esc = capslock

#space = overload(arrow_layer, space)
#
#[arrow_layer]
#h = left
#j = down
#k = up
#l = right

#h = home
#semicolon = end
#m = delete
#n = backspace
```
