# U-Net vs. DeepLabV3+ en el dataset MaSTr1325

Este repositorio contiene el código y los experimentos del artículo **"U-Net frente a DeepLabV3+: un caso de estudio en la base datos MaSTr1325"**.

El notebook `DeeplabvsUnet_MASTR1325.ipynb` implementa y compara dos arquitecturas de segmentación semántica para la navegación autónoma marítima:

1.  **U-Net (Ligera):** Una arquitectura tipo Encoder-Decoder entrenada desde cero.
2.  **DeepLabV3+ (Compleja):** Un modelo de estado-del-arte con un backbone Xception pre-entrenado en ImageNet.

## Hallazgos Principales

El estudio concluye que el modelo **U-Net** fue superior para este caso de uso específico, tanto en precisión como en velocidad.

* **Precisión (MeanIoU):** La U-Net simple (**0.8553**) superó al DeepLabV3+ (**0.8261**).
* **Velocidad (Tiempo Real):** En una prueba simulada con *Batch Size 1*, la U-Net (22.14 FPS) fue **3.4 veces más rápida** que la DeepLabV3+ (6.46 FPS).
* **"Trampa de la Precisión":** El trabajo expone cómo la métrica *Accuracy* (~98% para ambos) puede ser engañosa en datasets desbalanceados, a diferencia del *MeanIoU*.
* **Generalización:** Se demuestra que el modelo U-Net (entrenado en MaSTr1325) es altamente especializado y falla al enfrentarse a un "desplazamiento de dominio" (Domain Shift) al ser probado en el dataset LARS.

## Entorno y Uso

El notebook está diseñado para ejecutarse en **Google Colab** con un entorno de GPU (probado en NVIDIA Tesla T4).

* **Framework:** TensorFlow (v2.19.0) y Keras.
* **Bibliotecas Clave:** NumPy , Scikit-learn (para métricas), Matplotlib (para visualización).

## Datasets

* **Entrenamiento:** [MaSTr1325](https://www.vicos.si/resources/mastr1325/) - Para la detección de obstáculos en USVs.
* **Prueba de Generalización:** [LARS](https://lojzezust.github.io/lars-dataset/) - Un dataset con un dominio visual diferente (ríos y lagos).

## Autor y Agradecimientos

* **Autor:** Juan Miguel Martínez Muñoz, FIUNA.
* **Agradecimientos:** Las implementaciones base de las arquitecturas U-Net y DeepLabV3+ fueron proporcionadas por el Prof. Diego Palacios Riquelme.
