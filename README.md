# About
This tool uses an undocumented NVIDIA API, supported on Fermi and later, to convert colors before sending them to a wide gamut monitor to effectively clamp it to sRGB (based on the chromaticities provided in its EDID). AMD supports this as a hidden setting in their drivers, but NVIDIA doesn't because ???.

ICC profiles are also supported and can either be used to only remap the gamut (which is probably what you want when using a one not created by yourself) or for a full LUT-Matrix-LUT calibration, which should lead to great grayscale and color accuracy on (mostly) linear displays. Note that only the VCGT (if present), TRC and PCS matrix parts of ICC profiles are used. For accurate gamma calibration, profiles should be created with black point compensation disabled.

# Notes for use with EDID data
* If the checkbox for a monitor is locked, it means that the EDID is reporting the sRGB primaries as the monitor primaries, so the monitor is either natively sRGB or uses an sRGB emulation mode by default. If this is not the case, complain to the manufacturer about the EDID being wrong.

* The reported white point is not taken into account when calculating the color space conversion matrix. Instead, the monitor is always assumed to be calibrated to D65 white.
