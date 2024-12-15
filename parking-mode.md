# Parking Mode

{% hint style="danger" %}
DANGEROUS! Your partner will leave you, your car will steer into a group of crossing children, comma will hate you, and geohot will fart in your face after doing taco bell runs for a week using the secret good model.\
\
But seriously, don't do this unless you are offroad/testing
{% endhint %}

\
Random notes \[ToDo]

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

>
>
> 1. Once they see the logs that eps is reporting parking mode, it bans your device from further uploading. So no.
> 2. technically you can fool open pilot by lying about the status reported from steering. i.e. writing some additional code in the wp to say steering is performing regular lkas steering while in parking mode. But not sure how easy that is. (edited)

> have u tried to hold the sterring during a apa event. it is pretty easy. also have u seen the steering rate. it starts pretty slow and once it reachs >4NM(4.5NM max for apa) it really winds up fast. so unless u were dosing off it should be normal.

> There's definitely the potential for danger if the torque isn't nerfed properly, the wheel could spin full lock at 80mph

>
>
> 1. we are spoofing 6-7 different signals to get the eps into park assist mode.
> 2. _\[_&#x38;:08 P&#x4D;_]_&#x69;nfact the steering thinks we are in reverse gear ![😅](https://discordapp.com/assets/3bc4f2d1b8b9d29e732e.svg)
> 3. _\[_&#x38;:08 P&#x4D;_]_&#x61;nd the speed as 0
> 4. _\[_&#x38;:08 P&#x4D;_]_&#x73;o no way comma is going to be cool with it
> 5. _\[_&#x38;:10 P&#x4D;_]_&#x6C;uckily the apa steering torq msg has a factor of 4
> 6. _\[_&#x38;:10 P&#x4D;_]_&#x73;o every unit of lkas torq we send from comma, it gets requested as 4 times the value to the eps
> 7. _\[_&#x38;:12 P&#x4D;_]_&#x73;o we literally have to not touch openpilot code(except for the tuning). the white panda takes care of everything



<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>



