# AsProgrammer — CH347 second edition voltage fork

This is a fork of [nofeletru/UsbAsp-flash](https://github.com/nofeletru/UsbAsp-flash) (AsProgrammer)
that adds **1.8V / 3.3V programming voltage selection** for the **CH347 second edition** programmer
(the v2.x hardware whose firmware can switch VCC in software).

**Where:** select **CH347T** as the programmer, then use **SPI → Voltage → 1.8V / 3.3V**.
The choice is saved and re-applied to the device on startup and before every operation.

**How:** the CH347 v2 hardware drives its on-board VCC selector from **GPIO6**; this fork toggles it
with the standard `CH347GPIO_Set` call.

**SPI clock default:** this fork defaults the CH347 SPI clock to **15 MHz** (upstream defaults to
60 MHz). On typical socket/jumper wiring, clocks above 15 MHz can be unreliable and may produce bad
reads (e.g. an all-`FF` chip ID). You can raise it again under **SPI → Frequency** if your setup is
clean enough.

**Disclaimer:** this software is provided "as is", without warranty of any kind. You are responsible
for selecting the correct programming voltage for your target chip; using the wrong voltage may damage
your hardware. Use at your own risk.

For the original project documentation, supported chips, and protocols, see the
[upstream repository](https://github.com/nofeletru/UsbAsp-flash).
