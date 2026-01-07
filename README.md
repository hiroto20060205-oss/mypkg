# 擬似GNSSを使った仮想旅行パッケージ

## 概要
**東海道五十三次（日本橋〜京都三条大橋）を仮想的に旅行するためにGNSSデータ（緯度・経度）を配信・受信するROS 2パッケージです.**
**パブリッシャ内の配列内の異なる経緯度を持つ2点間の距離をステップ数に分けて計測することができます.**

## ノード
* **`gnss_simulator`**
    * **機能**: 定義されたルート（東海道五十三次）に従って、一定間隔で現在の緯度・経度を更新し、出力します.
    * **使用ライブラリ**: `GeoPy`（ポイント間の測地距離を計算）

* **`tour_guide`**
    * **機能**: GNSSデータを受信し、現在の位置情報や通過している宿場町の情報をログとして表示します.

## トピック
| トピック名 | メッセージ型 | パブリッシャ | サブスクライバ | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| `gnss_fix` | `sensor_msgs/msg/NavSatFix` | `gnss_simulator.py` | `tour_guide.py` | 現在の緯度・経度・ステータス情報を含む標準GNNSメッセージ型 |

## Geopyのインストール
```bash
sudo apt install python3-geopy
```

## 実行
```bash
ros2 launch virtual_travel tokaido.launch.py
```

## 必要なソフトウェア
- **python: 3.12.3**
- **GeoPy**

## 動作環境
- **Ubuntu 24.04.3 LTS**
- **ROS2 Humble**

## ライセンス
- © 2025 Hiroto Fujitake
- このパッケージはMIT licenseに基づいて公開されています.
- ライセンスの全文は[LICENSE](./LICENSE)から確認できます.

## 参考資料
- https://qiita.com/aquahika/items/6e3753d4498a190bddb1
- https://docs.ros.org/en/api/sensor_msgs/html/msg/NavSatFix.html
- https://geopy.readthedocs.io/en/stable/#module-geopy.distance
