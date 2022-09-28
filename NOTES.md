### Own notes

- PID controller [comes from ESPHome](https://esphome.io/components/climate/pid.html).
- I went for a PI controller instead due to the asymmetrical results in the autotune (check below).
- [Check here](https://github.com/ihormelnyk/opentherm_library/blob/master/src/OpenTherm.h) for other possible OpenTherm message IDs from this library.
- Some more possibly interesting sensor additions:
  - **Toutside** - Outside temperature (°C). I think it's only used to trigger the Boiler if the temp goes below a set threshold.


#### PID Autotune Results
```
PID Autotune Results:
  State: Succeeded!
  Could not reliable determine oscillation amplitude, PID parameters may be inaccurate!
    Please make sure you eliminate all outside influences on the measured temperature.
  Oscillation Frequency is not symmetrical. PID parameters may be inaccurate!
    This is usually because the heat and cool processes do not change the temperature at the same rate.
    Please try reducing the positive_output value (or increase negative_output in case of a cooler)
  Calculated PID parameters ("Ziegler-Nichols PID" rule):
 
  control_parameters:
    kp: 0.54373
    ki: 0.00007
    kd: 1038.79761
 
  Please copy these values into your YAML configuration! They will reset on the next reboot.
  Alternative Rules:
    Rule 'Ziegler-Nichols PI':
      kp: 0.40780, ki: 0.00003, kd: 0.00000
    Rule 'Pessen Integral PID':
      kp: 0.63435, ki: 0.00010, kd: 1454.31653
    Rule 'Some Overshoot PID':
      kp: 0.30177, ki: 0.00004, kd: 1537.42029
    Rule 'No Overshoot PID':
      kp: 0.18124, ki: 0.00002, kd: 865.66461
```