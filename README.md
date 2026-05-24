this is meant to connect gqrx and wsjtx each running in separate containers.

Each of these tools run X-Windows. You may need to run 
```bash
xhost +
```
first to allow for the windows to show.

## GQRX docker

https://github.com/KF8EEZ/gqrx-docker

In the `compose.yml` file you need to adjust the usb device id, this is what the limesdr mini looks like using `lsusb`: 
`Bus 002 Device 004: ID 0403:601f Future Technology Devices International, Ltd FT601 32-bit FIFO IC`

in the `compose.yml` section, edit under `gqrx:devices` section. The first number is the Bus and the second the Device that can be read from `lsusb` output.

```yaml
gqrx:
  devices:
    - "/dev/bus/usb/002/004" # <--- edit this line
```

run with podman
```bash
podman-compose run gqrx
```

if the particular usb device is not present you'll get an error:
```
Error: stat /dev/bus/usb/002/004: no such file or directory
exit code: 125
```

`gqrx` will automatically start to the gui interface.

For WSPR tuning on 20 meters, tune to 14_095_600 Hz. The LimeSDR has a large LO bleed through at the center frequency, so set the hardware RF LO off WSPR center and tune the receiver around off the center frequency. the LNAW antenna should be selected.

## WSJTX docker

https://github.com/KF8EEZ/wsjtx-docker

```bash
podman-compose run wsjtx
```

In the container run, but this should start automatically.
```bash
/wsjtx/output/bin/wsjtx
```

## References

https://www.kevinhooke.com/2019/09/07/running-wstj-x-on-a-raspberry-pi-using-an-sdrplay/



