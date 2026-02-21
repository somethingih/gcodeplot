Convert SVG (text is not supported; convert text to paths) and HPGL to gcode for a 3-axis GCode machine, 
where the Z-axis controls the pen height.


You can also convert the same SVG subset to HPGL.

Run with no arguments for some help.

Ender 3 V2 compatibility:

- Default machine profile is now `ender3v2` (Marlin-safe startup and `M0` pause command).
- To keep old behavior, use `--machine-profile=legacy`.
- Curves are smoothed by default (`curve-smoothing=0.35`) for more continuous plotting motion.
- Tiny disconnected paths are filtered by default (`min-path-length=0.30`) to reduce dot-like motion and excessive pen up/down.

Single-folder Inkscape install:

- Copy the `inkscape-gcodeplot` folder into your Inkscape user extensions directory (`%APPDATA%\inkscape\extensions` on Windows).
- Restart Inkscape.

Note on multiple pen usage:

The pen definition file is one-pen per line, in the format:

    n (x,y) svgcolor comment

Here, n is the pen number (pen 1 is assumed to be loaded at the start), (x,y) is the offset from the 
default pen position (note: gcodeplot.py will correct the offset and will NOT check for clipping at 
drawing edges--it is your responsibility to make sure your tool doesn't crash into anything due to 
offset), svgcolor is a color specification in svg format, e.g., rgb(255,255,00), #FFFF00 or yellow, 
and the comment is a human-readable comment.
