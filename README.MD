# YOLO 8 

## Veri setini oluşturalım

### Verileri etiketleme ve bölme

1. Windows işletim sistemi için [buradaki bağlantıdan LabelImg programını](https://github.com/tzutalin/labelImg/files/2638199/windows_v1.8.1.zip) indir.

2. Programı kullanarak etiketleme işlemini yap.

3. Yolo Data Splitter programını kullanarak verileri `test, val, ve train` olacak şekilde böl.

4. Oluşturulan etiketli veri setini zip dosyası olarak sıkıştır.

## CoLab

### Nvidia GPU ayarlarını yap.

#### Çalışma Zamanı (Runtime) menüsüne gir

1. Çalışma zamanı türünü değiştir (Change runtime type)
2. GPU seçeneğini seç ve kaydet

#### Nvidia-smi kontrolü yap

```
!nvidia-smi
```

#### Ultralytics paketini yükle

```
!pip install ultralytics
```

#### Gerekli paketleri içe aktar

```
from ultralytics import YOLO
import os
from IPython.display import display, Image
from IPython import display
display.clear_output()
!yolo checks
```

#### Config.yaml dosyasında path düzenlemesi yap

```
path: /content/datasets/veriseti/
```

#### Veri setini zipleyip colab'a yükle sonra aşağıdaki komutla zipten çıkar

```
!unzip zipliveriseti.zip -d datasets/veriseti
```

### Model eğitimine başla
```
!yolo task=detect mode=train model=yolov8m.pt data=/content/datasets/veriseti/config.yaml epochs=20 imgsz=640
```

### Tahmin

### Videoda nesne tespiti

#### videoyu yükle `/content/video/` içine yükle ve aşağıdaki komutla videoda nesne tespiti yap

```
!yolo predict model=/content/runs/detect/train5/weights/best.pt source="/content/video/cadir.mp4" imgsz=640
```
















