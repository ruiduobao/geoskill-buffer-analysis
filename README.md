# Buffer Analysis (geoskill-buffer-analysis)

> Vector buffer generation + fusion + overlay analysis + area statistics

---

## 1. Overview

Vector buffer analysis: generates buffers for point/line/polygon features, supports multi-feature fusion (unary_union/dissolve), overlay statistics against target layers, and area computation approximated with a local equidistant projection for geographic coordinates (km²).

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-buffer-analysis.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `buffers.geojson` | GeoTIFF/GeoJSON/JSON | Primary output |
| `dissolved_buffer.geojson` | GeoTIFF/GeoJSON/JSON | Primary output |
| `buffer_stats.json` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |


## 6. Technical Principle

- Point/line/polygon buffering (quad_segs)
- Buffer fusion and deduplication
- Overlay statistics + projected area computation

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
