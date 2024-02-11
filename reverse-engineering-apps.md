# Reverse Engineering Android APKs

It's something that i've tried and plan to explore more.  
This repo is only for my reference, so that i hopefully stumble upon it again, and dive into this madness once more.

## Commands Dump
Here are some commands that i've used for future reference.

### Extracting APK
```shell
# find the package name
adb shell pm list packages | grep paytm

# pull the apk (most likely a split apk)
adb shell pm path net.one97.paytm | sed 's/package://' | xargs -n1 adb pull

# merge the split APKs
java -jar APKEditor-1.3.3.jar m i *.apk -o paytm.apk

```

### Patching APK
```shell
pipx install objection
objection patchapk -s paytm.apk
objection --debug -g "net.one97.paytm" explore
# android ssl-pinning disable
```

Now that the APK is patched we can use mitmproxy to intercept the traffic and see what's going on.

