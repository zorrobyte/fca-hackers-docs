# Parking Mode

{% hint style="danger" %}
DANGEROUS! Your partner will leave you, your car will steer into a group of crossing children, comma will hate you, and geohot will fart in your face after doing taco bell runs for a week using the secret good model.\
\
But seriously, don't do this unless you are offroad/testing
{% endhint %}

How the jvepilot panda firmware works

#### **1. How `steer_type` is Selected**

`steer_type` is determined dynamically based on certain CAN messages and conditions:

* **`addr == 658`**:
  *   This CAN message determines **steer control type** and sets `steer_type`:

      ```c
      steer_control_type = (GET_BYTE(to_push, 0) >> 7) & 0x1;
      if (steer_control_type == 1) {
        if ((GET_BYTE(to_push, 0) >> 6) & 0x1) {
          steer_type = 1;  // LKAS Mode
        } else {
          steer_type = 3;  // Invalid or fallback
        }
      }
      ```
  * **`steer_type == 1`**: Enabled when `steer_control_type == 1` and a specific flag (`byte 0 >> 6`) is set.
  * **`steer_type == 3`**: Safety fallback when the above condition is not met.
* **`addr == 500`**:
  *   If `steer_control_type == 0`:

      ```c
      if (GET_BYTE(to_push, 2) >> 4 & 0x1) {
        steer_type = 1;  // LKAS Mode
      } else {
        steer_type = 3;  // Fallback
      }
      ```

***

#### **2. Differences Between `steer_type == 1` (LKAS) and `steer_type == 2` (APA)**

In **`safety_defaults`**, several functions send different CAN messages depending on `steer_type`.

**LKAS Mode (`steer_type == 1`):**

* **Purpose**: High-speed lane-keeping assist.
* **`send_steer_enable_speed`**:
  *   **`eps_cutoff_speed`** is set to `65 kph`:

      ```c
      eps_cutoff_speed = lkas_enable_speed >> 8 | ((lkas_enable_speed << 8) & 0xFFFF);
      ```
* **Message Behavior**:
  * It sends steering torque values and cutoff speed suited for higher-speed lane-keeping.

**APA Mode (`steer_type == 2`):**

* **Purpose**: Low-speed Automatic Parking Assist (APA).
* **`send_steer_enable_speed`**:
  *   **`eps_cutoff_speed`** is set to `2 kph`:

      ```c
      eps_cutoff_speed = apa_enable_speed >> 8 | ((apa_enable_speed << 8) & 0xFFFF);
      ```
* **APA-Specific Messages**:
  * The following functions are triggered **only when `steer_type == 2`**:
    * **`send_trans_apa_signature`**: Sends a gear command (`gear_R`).
    * **`send_shifter_apa_signature`**: Sends a shifter signal (`shifter_R`).
    * **`send_rev_apa_signature`**: Clears REV status.
    * **`send_wspd_apa_signature`**: Clears speed data.
    * **`send_count_apa_signature`**: Clears counters.
    * **`send_apa_signature`**:
      *   Sends a modified **APA-specific torque**:

          ```c
          int apa_torq = ((lkas_torq - 1024) * multi / 4) + 1024;
          to_fwd->RDLR |= 0x50;  // APA request
          to_fwd->RDLR |= 0x20 << 8 << 8;  // APA type = 1
          to_fwd->RDLR |= apa_torq >> 8;
          to_fwd->RDLR |= (apa_torq & 0xFF) << 8;
          ```
      * This message replaces steering commands to allow APA functionality.

***

#### **3. Message Differences: Summary**

| **Function**                 | **LKAS (`steer_type == 1`)**             | **APA (`steer_type == 2`)**                   |
| ---------------------------- | ---------------------------------------- | --------------------------------------------- |
| `send_steer_enable_speed`    | `eps_cutoff_speed` = 65 kph (128 factor) | `eps_cutoff_speed` = 2 kph (128 factor)       |
| `send_trans_apa_signature`   | Not used                                 | Sends `gear_R` in `RDLR`                      |
| `send_shifter_apa_signature` | Not used                                 | Sends `shifter_R` in `RDLR`                   |
| `send_rev_apa_signature`     | Not used                                 | Clears REV signal                             |
| `send_wspd_apa_signature`    | Not used                                 | Clears speed signals                          |
| `send_count_apa_signature`   | Not used                                 | Clears counters                               |
| `send_apa_signature`         | Not used                                 | Sends **APA-specific torque** and APA request |

***

#### **4. How the Messages are Sent**

When `steer_type == 2`:

* APA messages override standard steering signals for APA-specific controls.
* Speed thresholds, gear position, shifter states, and torque commands are modified for low-speed APA.

When `steer_type == 1`:

* Standard LKAS messages are sent with higher-speed torque and safety checks for lane-keeping.

***

#### **Conclusion**

In this combined code:

* `steer_type == 1` sends **LKAS messages** for lane-keeping assist at higher speeds.
* `steer_type == 2` sends **APA-specific messages** (gear commands, low-speed torque, and signal clearances) for Automatic Parking Assist.
* The **CAN messages** and their payloads are distinct between LKAS and APA, enabling different behavior for high-speed lane-keeping and low-speed parking.

Random notes \[ToDo]

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

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



