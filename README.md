# Nissan Fingerprint V2 - Testing Fork

## Install
You need to ssh into your device. Instructions on how to do that can be found here: https://github.com/commaai/openpilot/wiki/SSH

Once connected execute the following commands:

```
killall tmux
cd /data
mv openpilot/ openpilot_comma/
git clone --single-branch --branch nissan-fpv2-0.8.6 https://github.com/razem-io/openpilot.git
reboot
```

## Add your Fingerprint for your car

Follow the fingerprinting guide V2 still step 3: https://github.com/commaai/openpilot/wiki/Fingerprinting

Next please open an issue and copy the results of step 3 into the issue. We will need this to create a pull request with as many V2 fingerprints as possible. Also this will help to tackle possible issues early, before the pull request to the comma repository gets upstreamed.

Optional:

```
killall tmux && tmux new-session  'selfdrive/boardd/boardd' \; new-window 'selfdrive/car/fw_versions.py --scan'
```

This will give us debug information regarding the firmware. Please add these contents to the github issue aswell.
You can just enter `reboot` when finished.

### By opening an issue (slow but easy)

You won't need to do anything besides opening the issue. We will add your fingerprint and inform you when it is ready. Please subscribe to the github issue so that you will get updates!

### Manually (fast)

You can edit ./selfdrive/car/nissan/values.py and the results to FW_VERSIONS section. Once rebooted your car will kopefully get recognized by c2. Please open an issue anyway, to help us get your fingerprint into the next release.

## Uninstall
Connect to your comma via ssh and execute the following commands:

```
killall tmux
cd /data
rm -R openpilot
mv openpilot_comma/ openpilot/
reboot
```
