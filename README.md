# atlas-chiclana-data

Baked, pre-processed open data for the **Chiclana de la Frontera** map of [ATLAS](https://github.com/xandrsn/atlas-chiclana) (a playable 3D map built from public data). This repo holds only the files the game loads at runtime. Raw downloads, caches and the build scripts are not included; the scripts live in the generator repo.

Files are served raw from GitHub. Pin a release tag. `v1` holds the original renderer data; `v2` adds everything the v2 engine loads (below). Use `v2`:

```
https://raw.githubusercontent.com/xandrsn/atlas-chiclana-data/v2/data/<file>
```

Raw files are uncompressed, so no `Content-Encoding` is needed.

## Contents (`data/`)

| File | What | Source |
|---|---|---|
| `boundary.json` | Municipal limit (lon/lat rings) | OpenStreetMap relation 346951 |
| `dem.bin` | Terrain grid (IGN MDT05, resampled) | IGN MDT05 |
| `buildings.bin`, `roofs.bin`, `facades.bin` | Building footprints, floors, roof and facade colours | Catastro INSPIRE BuildingPart; OSM `building:colour`; PNOA sampling |
| `urban.bin`, `landclass.bin`, `grass.bin`, `trees.bin`, `trees_cells.bin` | Built-up land, land classes, lawn and tree positions | PNOA (classified), Catastro footprints |
| `walls.bin` | Rural plot boundaries | Catastro INSPIRE Cadastral Parcels |
| `pools.bin` | Swimming pool outlines | PNOA z19 colour segmentation |
| `osm.json`, `underground.json`, `tram/tram.json` | Roads, transport, tram | OpenStreetMap (Overpass) |
| `poi.json`, `plazas.json`, `plaza_mayor.json`, `plaza_mayor_spec.json`, `landmarks_osm.json`, `places/index.json`, `places_all.json` | Monuments, squares and places | OpenStreetMap, Wikidata (CC0), Wikimedia Commons (titles and coordinates) |
| `venues.json`, `venue_specs.json`, `football.json`, `courts.json`, `parks_all.json`, `promenade_raw.json`, `events.json`, `sancti.json` | Venues, sports pitches and courts, parks, promenade furniture, event sites, Sancti Petri islet | OpenStreetMap |
| `addresses.json` | Street addresses for the search box | Catastro INSPIRE Addresses |

## v2 additions (tag `v2`)

Everything the v2 engine requests at runtime, Chiclana only, same relative paths:

| Path | What |
|---|---|
| `cells/chiclana/` | Baked 3D cells (`c_<x>_<z>.bin`, 3527 files, about 1.4 GB) plus `index.json`, `levels.json`, `props.json`, `sports.json`, `tunnels.json` |
| `v2.json`, `maps.json`, `controls.json`, `quality.json`, `timecyc.json`, `events.json`, `peds.json`, `transit.json` | Engine configuration |
| `tram/tram.json` | Tram line and trams |
| `vehicles/` | Vehicle catalogue (`index.json` + one json per model) |
| `parking/chiclana.json`, `parking/chiclana.radar.bin` | Car parks and radar map |
| `peds/chiclana.json` | Pedestrian ways |

Sources and licences as below (OpenStreetMap, Catastro, IGN).

## Attribution and licences

- **Ortofoto PNOA** (served by IGN, not copied here): © Instituto Geográfico Nacional, **CC BY 4.0**.
- **Edificios, parcelas, direcciones**: © Dirección General del Catastro, **CC BY 4.0**.
- **Relieve**: MDT05 © Instituto Geográfico Nacional / CNIG, **CC BY 4.0**.
- **Calles, límites, POI, locales, parques**: © OpenStreetMap contributors, **ODbL**. Files derived from OSM are a derived database under the ODbL; keep the attribution and share-alike terms when you reuse them.
- **Monumentos**: Wikidata (**CC0**); Wikimedia Commons titles and coordinates (licence varies per file).

No personal data is included. Catastro addresses are public building addresses.

Generator and full pipeline: https://github.com/xandrsn/atlas-generator (see `docs/MAP_CREATION.md` there for the process).

---
Made by [Charlie Andersen](https://charlieandersen.vercel.app) · Game: [atlas-chiclana](https://github.com/xandrsn/atlas-chiclana) · Generator: [atlas-generator](https://github.com/xandrsn/atlas-generator)
