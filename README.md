this is meant to connect gqrx and wsjtx each running in separate containers.


## GQRX docker

https://github.com/KF8EEZ/gqrx-docker

In the compose file you need to adjust the usb device id, this is what the limesdr mini looks like using lsusb
Bus 002 Device 004: ID 0403:601f Future Technology Devices International, Ltd FT601 32-bit FIFO IC

## WSJTX docker

https://github.com/KF8EEZ/wsjtx-docker

## References

https://www.kevinhooke.com/2019/09/07/running-wstj-x-on-a-raspberry-pi-using-an-sdrplay/



