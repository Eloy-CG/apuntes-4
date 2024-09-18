## Notacións generales e problemas de OmNet
O grupo anterior ao teu da o mismo profesor, por si un día cuadra mal.
Usar a plantilla do TFG  do taboleiro para facer as memorias en LATex.
Os traballos entreganse por parexas.

- Windows: problemas con las extensiones de virtualización
  - Si aparece un error indicando que Intel VT-x/EPT no está soportado, se debe desactivar Hyper-V.
  Abre una terminal como Administrador, ejecuta el siguiente comando y reinicia Windows:
  ```msdos
  bcdedit /set hypervisorlaunchtype off
  ```
  - Para volver a activar Hyper-V:
  ```
  bcdedit /set hypervisorlaunchtype auto
  ```
  - Además, puede ser necesario desactivar la opción de integridad de memoria en Windows Security > Device Security > Core Isolation

## Tipografía das memorias:
• Cuida la redacción y la ortografía. Ambas serán tenidas en cuenta. 
• El único formato aceptado es PDF. 
• Utiliza la plantilla LaTeX Overleaf oficial del Trabajo Fin de Grado disponible en Taboleiro FIC. 
• Respecto a las figuras: 
o Referencia todas las figuras en el texto. 
o El contenido de las figuras debe ser legible sin necesidad de hacer zoom. 
o Utiliza el formato vectorial PDF para almacenarlas.  
o Las gráficas deben consistir en puntos de tamaño 1 sin que estén unidos por líneas. 
o Usa siempre el mismo color y forma de símbolo para cada serie de datos en todas las figuras. 
o Las leyendas deben tener un texto adecuado breve. 
o Los ejes deben tener títulos adecuados e incluir siempre sus unidades. 
o El rango de los ejes debe ajustarse para aprovechar al máximo el espacio de dibujo. P. ej., usar el 
rango [0,100] para el tiempo de simulación en las dos primeras secciones (explicadas más 
adelante) y [0,200] en las dos últimas, [0, 100] para el eje Y en la gráfica “Longitud de cola”, etc. 
Usar el mismo rango siempre que sea posible para poder comparar fácilmente de modo visual 
unas figuras con otras. 
o No deben incluir el título en la propia figura sino solo el pie de figura en la memoria LaTeX. 


## Configuracións generales do OmNet
**CONTRASEÑA DA MÁQUINA:** us3r
A lanzar na terminal da VM: 
```bash
sudo apt install libavcodec-dev libavformat-dev
```

En propiedades do proyecto, OMNET, project features activar as dúas Voice over Ip ... para que funcione a primeira práctica
