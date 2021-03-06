# hello_world_example

This example simply prints "hello world!" on the WiFi chips
internal console.

## How to run the example?

To run the example, first load the patched firmware and driver:
```
make reloadfirmware FWPATCH=hello_world_example
```

Then set up the wifi interface and print the firmware console:
```
adb shell "su -c 'ifconfig wlan0 down && ifconfig wlan0 up && \
  dhdutil -i wlan0 consoledump'"
```

The output of the firmware console should be:
```
start=0x001eb5cc len=0x00000800

RTE (USB-SDIO-CDC) 6.37.32.RC23.34.40 (r581243) on BCM4339 r1 @ 37.4/161.3/161.3MHz
000000.010 sdpcmdcdc0: Broadcom SDPCMD CDC driver
000000.016 hello world!
000000.020 reclaim section 0: Returned 48072 bytes to the heap
000000.068 hello_world_example (21.04.2016 13:14:44)
000000.073 wl_nd_ra_filter_init: Enter..
000000.076 TCAM: 256 used: 198 exceed:0
000000.080 reclaim section 1: Returned 71844 bytes to the heap
000000.086 sdpcmd_dpc: Enable
000000.095 wl0: wlc_bmac_ucodembss_hwcap: Insuff mem for MBSS: templ memblks 192 fifo memblks 259
000000.140 wl0: wlc_enable_probe_req: state down, deferring setting of host flags
000000.205 wl0: wlc_enable_probe_req: state down, deferring setting of host flags
000000.213 wl0: wlc_enable_probe_req: state down, deferring setting of host flags
```
