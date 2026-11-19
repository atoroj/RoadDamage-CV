# RoadDamage CV

Proyecto personal para **aprender visión artificial** desde cero. Mi objetivo es entender todo el proceso de un problema de detección de objetos: explorar los datos, prepararlos, entrenar un modelo y evaluarlo con métricas y gráficas.

Lo construyo paso a paso en un cuaderno de Jupyter, escribiendo yo el código y documentando lo que aprendo en cada celda.

## El problema

Detectar **daños en el asfalto** en fotos de carreteras. El modelo tiene que decir qué tipo de daño hay y dónde está, dibujando una caja alrededor de cada uno.

| Código | Daño |
|---|---|
| D00 | Grieta longitudinal |
| D10 | Grieta transversal |
| D20 | Grieta de cocodrilo |
| D40 | Bache |

## Dataset

Uso **[RDD2022](https://doi.org/10.6084/m9.figshare.21431547)** (Road Damage Dataset 2022), publicado para el reto CRDDC 2022. Tiene imágenes de varios países. Para empezar trabajo solo con las de **Estados Unidos**: 4.805 imágenes de 640 × 640 píxeles con 11.014 daños anotados.

Las imágenes no están en el repositorio por su tamaño. Para reproducir el proyecto:

1. Descargar RDD2022 desde [figshare](https://doi.org/10.6084/m9.figshare.21431547).
2. Descomprimir `United_States.zip` en `data/RDD2022/`, de forma que quede `data/RDD2022/United_States/train/...`.

## Librerías

| Librería | Para qué la uso |
|---|---|
| `pathlib` | Manejar rutas de carpetas y archivos |
| `xml.etree.ElementTree` | Leer las anotaciones en XML (formato Pascal VOC) |
| `collections.Counter` | Contar clases, tamaños y cajas |
| **matplotlib** | Gráficas del análisis y de las métricas |
| **OpenCV** | Leer imágenes y dibujar las cajas reales y las predichas |
| **Ultralytics (YOLO)** | Entrenar y evaluar el detector |
| **PyTorch** | El motor de deep learning que usa Ultralytics por debajo |

## Hoja de ruta

- [x] Organizar los datos y comprobar que cada imagen tiene su anotación
- [x] Leer los XML y analizar las clases (gráfica de cajas por clase)
- [ ] Analizar el tamaño de las cajas
- [ ] Convertir las anotaciones al formato YOLO
- [ ] Separar entrenamiento y validación
- [ ] Entrenar el modelo
- [ ] Evaluar: precision, recall y mAP por clase
- [ ] Gráficas de resultados con matplotlib

## Propósito final

Terminar con un modelo **YOLO entrenado por mí** que, dada una foto de una carretera, detecte y localice los cuatro tipos de daño. Quiero evaluarlo con las métricas propias de la detección de objetos (precision, recall y mAP, también por clase) y presentar los resultados con gráficas hechas en matplotlib: curvas de entrenamiento, métricas por clase, matriz de confusión y ejemplos de predicciones comparadas con las anotaciones reales.

Más allá del modelo, lo que busco es entender cada paso del proceso para poder aplicarlo después a otros problemas de visión artificial.

## Estructura

```
RoadDamage CV/
├── RoadDamage_EEUU.ipynb   ← cuaderno principal
├── README.md
└── data/                   ← dataset no subido a git por peso
```
