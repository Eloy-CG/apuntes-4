O grupo anterior ao teu da o mismo profesor, por si un día cuadra mal.
Usar a plantilla do TFG  do taboleiro para facer as memorias en LATex.
Os traballos entreganse por parexas.

- Windows: problemas con las extensiones de virtualización
  - Si aparece un error indicando que Intel VT-x/EPT no está soportado, se debe desactivar Hyper-V.
  Abre una terminal como Administrador, ejecuta el siguiente comando y reinicia Windows:
  '''
  bcdedit /set hypervisorlaunchtype off
  '''
  - Para volver a activar Hyper-V:
  '''
  bcdedit /set hypervisorlaunchtype auto
  '''
  - Además, puede ser necesario desactivar la opción de integridad de memoria en Windows Security > Device Security > Core Isolation

Configuracións generales do OmNet
