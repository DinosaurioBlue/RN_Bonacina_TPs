# Redes Neuronales — Trabajos prácticos

- `01_Softmax_Regression_20Newsgroups.ipynb`: TP anterior.
- `clasificacion_de_textos.ipynb`: notebook de clasificación de textos.
- `MLP_TP.ipynb`: copia de Softmax con el enunciado del nuevo TP al comienzo; pendiente implementar MLP.

## Trabajar en VS Code

Abrí `MLP_TP.ipynb`, seleccioná un kernel Python y ejecutá las celdas en orden. La primera celda de código usa `%pip install -r requirements.txt` para instalar en ese mismo kernel. En esta computadora se verificó con Python 3.14.5.

Los datos de 20 Newsgroups y los recursos de NLTK necesitan Internet en la primera descarga. Run All también ejecuta todos los experimentos heredados de Softmax, por lo que puede tardar.

## Guardar y subir cambios

Primero guardá los archivos en VS Code (Ctrl+S). Desde la terminal de esta carpeta:

```bash
git status
git add MLP_TP.ipynb
git commit -m "Avanzar TP de MLP"
git push origin main
```

`git push` requiere una sesión de GitHub válida en Git. Guardar un archivo no lo sube automáticamente. Los archivos `.ipynb` pueden incluir salidas: revisalas antes de publicar.
