---
name: geoskill-buffer-analysis
description: '矢量缓冲区生成+融合+叠加分析+面积统计'
---

# 缓冲区分析 | Buffer Analysis

Vector buffer analysis: generates buffers for point/line/polygon features, supports merging of multiple buffers (unary_union/dissolve), overlay statistics against a target layer, and area measurement approximated with a local equirectangular projection in geographic coordinates (km²).

## Core Algorithm / 核心算法

- Point/line/polygon buffering (quad_segs)
- Buffer merging and deduplication
- Overlay statistics + projected area measurement

## Dependencies / 依赖

```bash
pip install numpy rasterio scipy geopandas shapely
```

## Usage / 使用方法

### Example 1 (Synthetic Data, Offline)

```bash
python geoskill-buffer-analysis.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### Example 2 (Specified Area + Quiet Mode)

```bash
python geoskill-buffer-analysis.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### Example 3 (Real Input)

```bash
python geoskill-buffer-analysis.py --input <your data file> --output-dir ./out3
```

### Example 4 (Boundary Test with a Tiny Area)

```bash
python geoskill-buffer-analysis.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `buffers.geojson` | GeoTIFF/GeoJSON/JSON | Main output |
| `dissolved_buffer.geojson` | GeoTIFF/GeoJSON/JSON | Main output |
| `buffer_stats.json` | GeoTIFF/GeoJSON/JSON | Main output |
| `output-manifest.json` | JSON | Run manifest |

## Data Source / 数据源 / Source

- Synthetic mode: generates physically consistent simulated data locally, no external data source.
- Real mode: reads local input files, no network requests.

## Privacy / 隐私声明 / Privacy

- Runs fully offline by default; makes no network requests.
- `--synthetic` mode reads no external data.
- All computation is performed locally; no user data is uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
