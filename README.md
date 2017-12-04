Jelling is a simple daemon for Linux which receives OTP tokens from FreeOTP.

# Test Results

|   Device   |        OS        | Adv. | Connect | Discovery | Pair | GATT |
| ---------- | ---------------- | ---- | ------- | --------- | ---- | ---- |
|  iPhone 6+ | iOS 11.2         |  ✔   |    ✔    |     ✔     |  ✘   |  ✘   |
|   Nexus 5x | LineageOS 14.1   |  ✔   |    ✔    |     ✘     |  ✘   |  ✘   |
|      Pixel | Android 8.1 beta |  ✔   |    ✘    |     ✘     |  ✘   |  ✘   |

# How to Test

1. Make sure your phone and computer are **NOT** paired.

2. Start Jelling on your computer.

3. Install and open LightBlue on your phone.


4. Does LightBlue see your computer within a few seconds (<30)? If so,
   advertisement is working.

5. Click on your computer in LightBlue. Does it successfully connect? Do you
   see Jelling among the list of services[^1]? If so, connection and service
   discovery are working. If not, you'll have to get Bluetooth packet logs to
   see whether connection or service discovery is failing.

6. Click on the service.[^1] Do you see the Jelling characteristic?[^2] Is it
   listed as write-only? If so, discovery is working.

7. Attempt to perform a write operation in LightBlue against the
   characteristic.[^2] A good test value is `30` (which is hex for `0` in
   ASCII). Does the device attempt to pair? Does it succeed? If so, pairing is
   working.

8. If pairing succeeds, perform the previous step again. This time, instead of
   pairing it should perform the actual GATT write. Does your computer type
   `0`? If so, the GATT write is working.

9. Submit a pull request which updates the above table with your test results.

[^1]: The Jelling Service UUID is: `B670003C-0079-465C-9BA7-6C0539CCD67F`
[^2]: The Jelling Characteristic UUID is: `B670003C-0079-465C-9BA7-6C0539CCD67F`
