# Panda Firmware

Notice the filenames at the top. Left Sunny advanced, Middle jvePilot, right xps\_seps

<figure><img src="../.gitbook/assets/Screenshot 2024-12-15 092716.png" alt=""><figcaption></figcaption></figure>

steer\_type ==1 spoofs the speed going to EPS to enable LKAS control under 39mph\
steer\_type == 2 is APA mode (parking mode)\
steer\_type == 3 is stock/OP default with 39MPH lockout

<figure><img src="../.gitbook/assets/Screenshot 2024-12-15 092739.png" alt=""><figcaption></figcaption></figure>

jve has dynamic enable/disable so steering isn't heavy as we spoof the EPS speed only when enabled, the note that the steering wheel needs a moment to adjust torque is likely due to a ramp/interp function on the torque/speed lookup map on the EPS

<figure><img src="../.gitbook/assets/Screenshot 2024-12-15 092749.png" alt=""><figcaption></figcaption></figure>

jve has the most up to date and feature rich panda code at this time, imo (12/15/2024)

Sunny doesn't seem to have an op long implementation for FCA but need to read the code more
