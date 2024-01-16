# Planetiler Transitopia Base Map Profile

This profile for [Planetiler](https://github.com/onthegomap/planetiler) is used to create the base map (the background map) used for
[Transitopia](https://www.transitopia.org). It is a _slightly_ modified version of the
[OpenMapTiles Planetiler Profile](https://github.com/openmaptiles/planetiler-openmaptiles).

## How to run

After [installing Java 21+](https://adoptium.net/installation.html):

```bash
# Build the project (use mvnw.cmd on windows):
./mvnw clean package
# Then run:
java -jar target/planetiler-*-with-deps.jar --force --download --area=british-columbia --exclude-layers=housenumber,mountain_peak,poi,building --output=data/transitopia-base-bc.pmtiles
```

See [Planetiler README.md](https://github.com/onthegomap/planetiler/blob/main/README.md) for more description of the
available options.

## Differences from OpenMapTiles

In addition to the [upstream differences between `planetiler-openmaptiles` and `openmaptiles`](https://github.com/openmaptiles/planetiler-openmaptiles#differences-from-openmaptiles):
- The **`park`** layer includes [`leisure=park`](https://wiki.openstreetmap.org/wiki/Tag:leisure=park?uselang=en) areas (e.g. municipal parks) and excludes `boundary=aboriginal_lands` and many [`boundary=protected_area`](https://wiki.openstreetmap.org/wiki/Tag:boundary=protected%20area?uselang=en) that aren't parks (e.g. heritage neighborhoods)
    - For example, in the Transitopia version: [Queen Elizabeth Park](https://www.openstreetmap.org/way/23393985) in Vancouver is considered a park, and the [Abbott Street Conservation Area](https://www.openstreetmap.org/relation/12804767) and [Sen̓áḵw lands](https://www.openstreetmap.org/relation/11984710) are not.

## Customizing

See [the upstream documentation about how to customize](https://github.com/openmaptiles/planetiler-openmaptiles#customizing) the map.

## License

All code in this repository is under the [BSD license](./LICENSE.md) and the cartography decisions encoded in the schema
and SQL are licensed under [CC-BY](./LICENSE.md).

Products or services using maps derived from OpenMapTiles schema need to visibly credit "OpenMapTiles.org" or
reference "OpenMapTiles" with a link to https://openmaptiles.org/. Exceptions to attribution requirement can be granted
on request.

For a browsable electronic map based on OpenMapTiles and OpenStreetMap data, the
credit should appear in the corner of the map. For example:

[© OpenMapTiles](https://openmaptiles.org/) [© OpenStreetMap contributors](https://www.openstreetmap.org/copyright)

For printed and static maps a similar attribution should be made in a textual
description near the image, in the same fashion as if you cite a photograph.
