1. 将 OSM PBF 转为 GeoJSON
OSM 的 .pbf 文件不能直接用 Node.js 解析。推荐用 osmium 或 osmtogeojson 先转成 GeoJSON。
安装 osmium（推荐，需本地支持 C++ 环境）
Apply to camera.json
Run
brew install osmium-tool  # Mac
# 或 apt install osmium-tool  # Ubuntu
osmium export beijing-latest.osm.pbf -o beijing-roads.geojson -f geojson --output-header=type=FeatureCollection
只导出道路（可选）：
osmium tags-filter beijing-latest.osm.pbf w/highway -o roads.osm.pbf
osmium export roads.osm.pbf -o beijing-roads.geojson -f geojson 
2. Node.js 脚本：查找违禁点缓冲区内的 way id
安装依赖
Apply to camera.json
Run
turf

npm install @turf/turf
