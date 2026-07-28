# PTP Fresnel Zone Planner

A simple map tool for planning point-to-point wireless links.

> [!WARNING]
> This is a **vibe-coded project** created for personal use (including this readme). It has not been professionally
> engineered, independently
> validated, or tested for every device and environment.
>
> In my own 2.4GHz PTP setup, using the tool to identify and clear branches from the Fresnel zone improved the average
> received
> signal from approximately **-78 dB to -70 dB**. This is one personal result and does not guarantee the same
> improvement
> for other links. The signal could probably have been improved even further, but there were some trees we did not want
> to
> prune/remove to get a clearer fresnel zone.

Use it online here:

**https://jonathanwiklund.com/fresnel-zone**

Choose the location of **Point A** and **Point B**, select the radio frequency, and the tool shows the approximate first
Fresnel zone between the two antennas.

By allowing location access you can walk around the zone and cut branches inside it. (**make sure you own the land /
have permission to cut the branches**)

## Why this is useful

A wireless link can have a clear visual line of sight and still perform poorly if branches, trees, buildings, or other
objects extend into the Fresnel zone.

This tool helps you see how wide the Fresnel zone is along the link. You can then use the map together with what you see
on site to decide:

- Which branches may need to be cut back
- Whether moving an antenna could improve clearance
- Whether raising or lowering an antenna may help
- Which parts of the path deserve closer inspection
- How the Fresnel zone changes between 2.4 GHz, 5 GHz, 60 GHz, and other frequencies

This can be especially useful when aligning outdoor point-to-point devices such as the TP-Link CPE210.

## Features

- Set Point A and Point B by tapping the map
- Move the points by dragging them
- Use the phone or browser's current GPS location
- Show the current GPS accuracy
- Show the distance between the two points
- Draw the first Fresnel-zone footprint
- Show the maximum Fresnel radius
- Show the commonly used 60% clearance radius
- Frequency buttons for common bands
- Custom frequency option
- Mobile-friendly and collapsible controls
- Points are saved in the browser after a refresh
- No backend or build process required

## How to use it

1. Open **https://jonathanwiklund.com/fresnel-zone**.
2. Press **Set A** and tap the location of the first antenna.
3. Press **Set B** and tap the location of the second antenna.
4. Select the frequency used by the link.
5. Check the width of the Fresnel zone.
6. Compare the shaded area with trees, branches, buildings, and other possible obstructions along the path.

You can drag Point A or Point B while the toolbar is open. Collapse the toolbar when you are finished to avoid moving
the points accidentally.

The points are stored in `localStorage`, so they remain after refreshing the page. Press **Clear** to remove them.

## Run it locally

The project is a single HTML file:

```text
ptp-fresnel-planner.html
```

Start a small local web server:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/ptp-fresnel-planner.html
```

Geolocation normally requires HTTPS or `localhost`.

## Fresnel zone

The app draws the first Fresnel zone as a top-down area on the map.

The zone is widest near the middle of the link. Lower frequencies create a wider Fresnel zone, while higher frequencies
create a narrower one.

The displayed 60% value is a useful clearance reference. In practice, keeping most of the Fresnel zone clear generally
gives the link a better chance of performing well.

## Limitations

The map shows the Fresnel zone from above. It does not know the actual height of branches, trees, buildings, terrain, or
antennas.

It does not currently include:

- Antenna height
- Terrain elevation
- Tree or building height
- Earth curvature
- Signal strength
- Interference
- Transmit power
- Receiver sensitivity
- Antenna direction or gain

Use it as a practical planning aid, not as a guarantee that a link will work.

For example, if the shaded zone crosses a group of trees, the tool can help identify where branches may be affecting the
link. You still need to inspect the real path and consider the vertical clearance.

## GPS and privacy

The app asks the browser for high-accuracy location data and shows the accuracy reported by the device.

Point A and Point B are stored only in the browser using `localStorage`. The project has no application backend.

Leaflet resources and OpenStreetMap map tiles are loaded from external services.

## Dependencies

- [Leaflet 1.9.4](https://leafletjs.com/)
- [OpenStreetMap](https://www.openstreetmap.org/)

## Project files

```text
.
├── README.md
└── ptp-fresnel-planner.html
```

## License

This project is licensed under the [MIT License](LICENSE).