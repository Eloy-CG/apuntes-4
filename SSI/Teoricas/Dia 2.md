# Tema 1: Criptología

A criptología e a área de estudio constituida polos diferentes esquemas de cifrado. Podemos dividir a criptografia en 3 etapas:

- Precientifica (Antiguedad - 1949)
- Cientifica (Shannon): 1949-1976 -> Revolución de concepto, simetría, unha clave para cifrar e descifrar
- Asimetrica (Diffie-Hellman): 1976-actualidad -> o primeiro algoritmo de cifrado que o consigue é RSA
- Cuantica
- Post-Cuantica

Ás técnicas usadas para descifrar un mensaje sin conocimientos dos detalles do cifrado chamamoslle **criptoanálisis** (non confundir con descifrado, que é un proceso normal usando a clave).

- ***Anotación**: interesante mirar leccións de Intypedia sobre criptografía.*

## Edad Precientífica

- Polybios foi un dos primeiros algoritmos de cifrado da historia, data do s. II a.C.
  Basicamente consiste nun algoritmo de tipo **sustitución monoalfabético**, donde cada letra sustituyese polas suas coordenadas nunha tabla:

  ![image](https://github.com/user-attachments/assets/1f6d43ec-dcf9-44c6-a2fb-3bf09cbc9ce6)
  HOLA = 32 43 13 11


- O algoritmo César (s I a.C.) tamén era un algoritmo de sustitución monoalfabética donde cada carácter sustituese polo que está 3 posicións despois. Exemplo:
  HOLA = OLSSV
  Este algoritmo é facilmente codificable como:

  ```E:Encrypt C=E(p)=(p+3)mod26 D:Decrypt p=D(C)=(C-3)mod26```

  E cun desplazamento variable: 

  ```E:Encrypt C=E(p)=(p+k)mod26 D:Decrypt p=D(C)=(C-k)mod26```
