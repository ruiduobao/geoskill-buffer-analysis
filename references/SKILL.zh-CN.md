# 缓冲区分析 | Buffer Analysis

矢量缓冲区分析：对点/线/面要素生成缓冲，支持多要素融合（unary_union/dissolve）、与目标层叠加统计，以及地理坐标下用局部等距投影近似的面积量算（km²）。

## 核心算法

- 点/线/面缓冲（quad_segs）
- 缓冲融合去重
- 叠加统计 + 投影面积量算

## 依赖

```bash
pip install numpy rasterio scipy geopandas shapely
```

## 使用方法

### 示例 1（合成数据，离线）

```bash
python geoskill-buffer-analysis.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### 示例 2（指定区域 + 静默）

```bash
python geoskill-buffer-analysis.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### 示例 3（真实输入）

```bash
python geoskill-buffer-analysis.py --input <你的数据文件> --output-dir ./out3
```

### 示例 4（极小区域边界测试）

```bash
python geoskill-buffer-analysis.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## 输出

| 文件 | 格式 | 说明 |
|---|---|---|
| `buffers.geojson` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `dissolved_buffer.geojson` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `buffer_stats.json` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `output-manifest.json` | JSON | 运行清单 |

## 数据源 / Source

- 合成模式：本地生成物理一致的模拟数据，无外部数据源。
- 真实模式：读取本地输入文件，无网络请求。

## 隐私声明 / Privacy

- 默认完全离线运行，不发起任何网络请求。
- `--synthetic` 模式不读取任何外部数据。
- 所有计算在本地完成，不上传用户数据。

## License

MIT
