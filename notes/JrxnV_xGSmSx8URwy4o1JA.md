ML-crawler0823會議紀錄
===

###### tags: `ML` `AI`

:::info
- **Meeting連結:** https://meet.jit.si/SeparateAchievementsFunctionAhead
- **日期:** 2022/08/23
:::

## 紀錄 
Image source https://www.planet.com/nicfi/

Google earth engine with preprocessing https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR#image-properties

Model structure https://github.com/qubvel/segmentation_models

Pretrain on Open Street Map data

* Unet的效果看起來不錯
* 相較於只用可見光訓練模型，由於建物和土地的反射光不在不可見光的部分差異更大，對於訓練埋形來說效果更好，可以考慮使用解析度稍微低一點但是有包含可見光以外光譜資訊衛星圖來訓練