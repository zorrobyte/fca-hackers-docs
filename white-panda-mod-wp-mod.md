# White Panda Mod (WP Mod)

## Disclaimer

This guide is intended for **educational purposes only**. Some modifications are strictly for **off-road or experimental use**. Certain changes may:

- Be **dangerous** and impair vehicle safety.
- Violate **U.S. federal, state, or local laws** (e.g., emissions standards or tampering regulations).
- **Void warranties** or damage your vehicle.
- Result in a ban from services such as **Comma Connect** or **Cabana**.

By using this guide, you agree to accept full responsibility for your actions and absolve the author of any liability for damage, injury, or legal consequences.

---

# White Panda Pacifica Mod Instructions

The instructions below are for the hardware portion of the White Panda Pacifica Mod to allow Pacificas to steer to zero and increase torque. This modification involves flashing and attaching a Comma White Panda (WP) to a custom OBDII wire harness, which is wired to the star connector in the glove box, and a 12v power source to power the WP.

## Supply List

[https://discord.com/channels/812934069591080962/821388732820094987/829069554449383455](https://discord.com/channels/812934069591080962/821388732820094987/829069554449383455)

You will also need some 20 AWG wire and connectors to bridge this wire to the OBDII harness. Note that this connection is crucial, and should be made as solid as possible to prevent power interruption.

---

## STEP 1: Flash WP and Install `xps_fca` on Comma 2

You will want to first flash the White Panda (WP) with this branch:
- [https://github.com/xps-genesis/panda/tree/xps_seps](https://github.com/xps-genesis/panda/tree/xps_seps)

Then install this branch on your Comma 2:
- [https://github.com/xps-genesis/openpilot/tree/xps_fca](https://github.com/xps-genesis/openpilot/tree/xps_fca)

---

## STEP 2: Create the OBDII Harness

First, prepare the OBDII harness using this pinout diagram:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfbUCO_8WNy4qXbiiPtJcL_1s9aoNFiO1uyez_MiaX7uUr28ZXE1OZ2UXm6eK7-7V3It8JVscO46sG6ePqBJ2GfvOZOQyPpCk1SoIjFL_t9mGsaeZ7yADGNsM5wsAf-r1Ih6XJnDg?key=CZYD9DMG4nwTT44olpFjHuzz)

Find these wires on the harness, and mark them with tape for identification; you should have 3 pairs of wires once complete. Attach the metal connectors to the four CAN1 H/L and CAN3 H/L wires, then place them into the plastic star connectors as shown below:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdevNbDOSRys1WtJNBCNAKXqDKJMwI06zT4h4AUmc9owLy3Lh2rn-alEHTy1U_XVeIhYZyYUdMNLGFCkvdCAbraohDywLLDCJHA2nvuF0kYNRxwUONsws9J4D8kdaPYiuAFJogx3w?key=CZYD9DMG4nwTT44olpFjHuzz)

You should have a harness similar to this once you are done:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdOc7GQY3FPDOr3SMfNaezkgq7LWUAXUL5R9yi9eufzHwy4odHGPgbKVIxLvdUK1qAoSnZ_EfokcDHRq7TTaVGlTOVsnArbiqGuQ04aeZDRfib8VjsaqOg5bEve7UUyQ4W4zU1YgQ?key=CZYD9DMG4nwTT44olpFjHuzz)

---

## STEP 3: Prepare New Star Board (eBay Star Board)

To avoid confusion, we’ll refer to this board purchased for the mod as the eBay star board. First, remove the white backing off the eBay star board, then cut off the second tab as shown:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXesM0ZcEKfNubMOaYvBJFHxoc3O0CaS3gKD4F3Yqy-eOMTdm-KIkGnqDmw-NKgVVxys_5aEaAFmf26RjMZhiVAMrV4vmEnIdWSEbxjGMaOrG1GqEz-g8cNjjYaFUEAlqERq8_-YJw?key=CZYD9DMG4nwTT44olpFjHuzz)

Then, on the back of the eBay star board itself, use a small file or Dremel to carefully sever the connection to the other connectors on the board:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXejZhs_zLH-IZhSIoQhj12ibXQD17IdGQMVAFp0gT9xeQIAGQ1Lfnpk530Q1sZI6ubpfEql8Pzk7AV_MUinOdHUprDrlz-AeUyta5yZ9MeTFV_vJKYd4TJB44xqx1c9M446PL01-A?key=CZYD9DMG4nwTT44olpFjHuzz)

Replace the white back and the eBay star board is ready for installation.

---

## STEP 4: Locate and Tap into 12v Switched Power

Remove the plastic cover by carefully prying around the USB panel with a plastic trim tool, then remove the harness from the USB:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdwg8WgZ-bpDCu9atpmSlX3wzme68Fl0EMgErcGfVcnYqcqeh67N_ORHbKSiA-8yTa7W0ihsw0N_uKQXiy2dhHpL0LKvZmNVTcQbV71hf_-wpY6PLaebQD6wgIoaG7KbKz8aMsdEg?key=CZYD9DMG4nwTT44olpFjHuzz)

Now, using the plastic trim remover tool, remove this side panel in the passenger footwell:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcx9VQpPaLAi0qb0_w_G06Zw-QvmOqOlylb_qMVaP3k9sv-X-0oh73V5XF9hCwrVrxRdbrSdUX7nPDOB4oX1bfu0NPkV5Hq5gMhtbxp_SxbNSg0eWaedwHwiDCTSpsK9sOmjtOz?key=CZYD9DMG4nwTT44olpFjHuzz)

The video link below shows how to remove the glove box and fabric backing to access the space behind the glove box and the star connector. Note that pushing in the tabs on the sides of the glovebox to drop it for the first time requires a lot of force, and this is normal.

- [How To Change 2017 - 2021 Chrysler Pacifica Cabin Air filter - Replace Remove Replacement Location](https://www.youtube.com/watch?v=U5MnSaoD4eY)

Connect the Posi-Tap Connectors as shown below. On the USB harness, the pink wire is hot, black wire is ground—verify with a voltmeter. Run your 12v wire from the USB through the access panel, up into the glove box area. Use zip ties or velcro straps to affix the wire as you go to minimize movement of the wires. You can replace the USB harness and pop the USB panel back in once you have run the wire.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeSMiGKJhDgBaNmnp72Phc0qPKBvR6_V8SM9DNdgy3srRYWHcaovipZWjEBuIntnxuLKbdr_wmbgxaKFjCJjUDgB_aZwFrXbpM0M1M322uZ3-FzsWm5vUkzIRZLyEpK-PZj6VGj?key=CZYD9DMG4nwTT44olpFjHuzz)

---

## STEP 5: Install eBay Star Board, OBDII Harness, and 12v Power

Now that the 12v wires are in the area where we will be installing the harness, you can wire the hot and ground to the OBDII harness. Solid, automotive-grade connectors are recommended for this task, as we want to ensure a solid connection and power. Note: if the WP loses power while operating the vehicle, you will lose power steering.

Look up into the cavity and you will see the star connector we will be patching into:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc7aeozGi5hpnM1JV6fPtBnMl2yTvuWcDDwei6hV3iBa7MweYOX-m_9d57GqeVdGVijQ3hPq4kJuXYtqontU_EgxeBO8WggyStV9NJu_h7mtffIKgMrFz3szW7gQnoUbRl7L88vgA?key=CZYD9DMG4nwTT44olpFjHuzz)

The star connector is the large green board with multiple wiring harnesses coming from it. The red outline in the example photo shows where we will be placing the eBay star board for this mod:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfS_aC2wSSfg8JU6ss67qk7g5kLabmUkI0wU1H4b2B5V-jREPMS4EQcsXahOBXtTxrcCVRv6eX2it2acZ4LWmPOP11PHy7Awnt6cEm1FucO8SQP0VBjwxdlVI6jLOMDK_bRGyZV?key=CZYD9DMG4nwTT44olpFjHuzz)

The photos above show how the eBay star board clips in place, and also the EPS (Electronic Power Steering) wire harness, which has a yellow and yellow/brown wire. If you have any doubts about which wire it is, remove the likely suspect, then turn on the vehicle. With the EPS removed, the power steering will be off, and there will be a warning light on the dash indicating there is no power steering:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXey2e0YLr1dsAlkclIJMcdvCcqpYnmXmqTOkFngkjARcUrw9CgKQbTBtV1T2Eo36sDtB7xaBYZv8XKh4fPFWjxOQFp8vaPfIfeb6_tmveodchPlfCg6AlNNGK8x-yMnm3klZfqUzw?key=CZYD9DMG4nwTT44olpFjHuzz)

Remove the EPS from the Pacifica star board, then plug it and the CAN3 connector from the OBDII harness into the eBay star board:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfi7uThynAdPePvMMV9pkcv_xQ4LU_Rlsm2A7Tv9GOMl9u8IZi4_5YknV7ptcrLfaJ2_hBctzI-hih_r9H3S5e0fsUZZXzV5wipVTzu1UZihjwtX0CaE6ozX8JK-idobRxTdIPuOw?key=CZYD9DMG4nwTT44olpFjHuzz)

The CAN1 connector from our harness goes into the Pacifica star board to replace the EPS connector. Now the harness should be connected to 12v power and wired into the vehicle star board. Attach the WP to the OBDII harness, and use zip ties or velcro to secure the harness and minimize movement.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXf1gr6QqlLR-43FIZzLpg6OboUNrlOkBezKnG01h9lZeYntpsRYSmJk2GKI02BVi4p8XQ7Ytu14s5MBCfDUkFwsLdYVZtUz6mKRVsOsPwNBhJFA3YE0kZWlf9xLbRsRc5cyX1ci?key=CZYD9DMG4nwTT44olpFjHuzz)

To allow ease of access for flashing WP in the future, you can run a USB-A cable back from the WP into either the glovebox or behind the passenger footwell panel:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfooxiO9weoJrYV5eRvpgfaOjim4VXt-P59ZiLB01tQae0gdnPEHQXprcxZqqb8yANjicwPy3LUm7ConapqeSZ34x8P0UuYTDCsf_u8fK2lEVo70ukD_hKjzAjkKlB_NIzMIPRGYQ?key=CZYD9DMG4nwTT44olpFjHuzz)

Here’s another option for storing the WP and OBDII harness to be secure and out of the way:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdNU71OEftPhaq7yR2FZqJQQOmRknpIVw9XRGldoE1fL9eRhV9zKYEvmc6HWByNCVPTOurgp-uL2tX7yKK1qHXHInDYosh0U4R98jM9yjxkvy4rPOsVkoKbEZUbhvrMYb9M4YoiaA?key=CZYD9DMG4nwTT44olpFjHuzz)

At this point, you can turn the vehicle on, verify you don’t have any EPS error messages on the dash, and confirm power steering is working. Replace the panels and glovebox, and you are done!
