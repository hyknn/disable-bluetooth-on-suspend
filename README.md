## Disable Bluetooth on suspend in Linux

To disable Bluetooth on suspend in Linux, you can add a script to the /lib/systemd/system-sleep/ directory. The script should contain the command "rfkill block bluetooth" to block the Bluetooth device, and "rfkill unblock bluetooth" to unblock it.

You can create the script by running the following command:

```
sudo nano /lib/systemd/system-sleep/disable-bluetooth.sh
```

Then paste the following content:

```
#!/bin/sh
case $1 in
        pre)
                rfkill block bluetooth
                ;;
        post)
                rfkill unblock bluetooth
                ;;
esac
```

Make the script executable:

```
sudo chmod +x /lib/systemd/system-sleep/disable-bluetooth.sh
```

This should disable Bluetooth on suspend and re-enable it on resume. To check the current state of the Bluetooth, you can use the command "rfkill list"

Please note that the above method is a general way, Depending on your Linux distribution and version, the steps may vary.

### Credit
Generate by ChatGPT
