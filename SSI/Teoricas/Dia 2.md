# Tema 1: Criptología

A criptología e a área de estudio constituida polos diferentes esquemas de cifrado. Podemos dividir a criptografia en 3 etapas:

- Precientifica (Antiguedad - 1949)
- Cientifica (Shannon): 1949-1976 -> Revolución de concepto, simetría, unha clave para cifrar e descifrar
- Asimetrica (Diffie-Hellman): 1976-actualidad -> o primeiro algoritmo de cifrado que o consigue é RSA
- Cuantica
- Post-Cuantica

Ás técnicas usadas para descifrar un mensaje sin conocimientos dos detalles do cifrado chamamoslle **criptoanálisis** (non confundir con descifrado, que é un proceso normal usando a clave).

- ***Anotación**: interesante mirar leccións de Intypedia sobre criptografía.*

## Edad Precientífica pt1

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
  Cabe destacar que este algoritmo e fácilmente descifrable por forza bruta. Solo ten 25 combinacións  posibles

**Todos os algoritmos teñen unha clave**, nos dous casos anteriores son implícitas. Para Polybios sería a tabla e para César sería o desplazamento.

- ROT13 é un algoritmo equivalente a facer un César con k=13. Polo tanto, ten a particularidad de  que a cada carácter corresponde o carácter a mitad de tabla (13 = 26:2)

### Cifrados por sustitución monoalfabeto

O caso xeneral para este tipo é aquel no que podemos escoller unha clave aleatoria (clave de sustitución) da misma lonxitude que o alfabeto.
Sempre que o algoritmo de cifrado non sea simple e escollido a man si non que sea aleatorio imposibilitase a forza bruta pola alta posibilidade de combinanción no diccionario.

#### ¿COMO O EXPLOTAMOS ENTONCES? **Análisis de frecuencias**

Esta técnica basase en explotar a redundancia do lenguaje. Para un idioma dado, si collemos textos ao azar e observamos os porcentaxes de aparición de cada letra observamos:

- Unhas letras son máis frecuentes que outras.
- A frecuencia mantense entre textos.
- Tamén os conxuntos de dous ou tres letras teñen unha frecuencia diferente e manténse entre textos.

Nun texto cifrado con sustitución monoalfabeto a frecuencia de caracteres mantén a mencionada anteriormente, polo tanto realizando a sustitución de caracteres pola porcentaxe de aparición podemos descifrar o texto codificado.

#### Cryptool

Programa gratuito e open-source para aprender criptografía e criptoanálisis. Permite visualizar algoritmos como César,Enigma,RSA,Diffie-Hellman, firmas digitales,DES,AES... Tamén permite analizar algoritmo criptográficos.


### Playfair

- Playfair é o un algoritmo de sustitución poligráfica aparecido no siglo XIX d.C. que nace que idea de romper ca técnica de  sustitución estadísticas para romper o algoritmos hasta entonces. O cambio que introduce é que realizando sustitucións dobles evitando a clave. Exemplo:


  ![image](https://github.com/user-attachments/assets/31cfbf49-ebc3-474f-9a2c-7a2b74252351)


  Crease a matriz insertnado unha clave e completando co abecedario sin a clave. Despois tomanse os carácteres de dous en dous e procedese:
  - Si m_1,m_2 na misma fila -> C_1,C_2 son os dous caracteres da dereita. Exemplo: ft -> LZ
 
  

  a. Si m_1,m_2 na misma columna -> C_1,C_2 son os caracteres de abaixo
  b. Si m_1,m_2 en filas/columnas distintas -> C_1,C_2 son os caracteres da diagonal desde m_1
  c. Si m_1=m_2 añádese un separador (normalmente unha X)
  d. Si o número de carácteres é impar, añadese un caracter final (normalmente unha X) 
 
O descifrado aplica as mismas reglas que o descifrado pero:
  - regla a): en lugar de sustituir por los caracteres de la derecha, se sustituyen por los de la izquierda, y
  - regla b): en lugar de sustituir por los caracteres de abajo, se sustituyen por los de arriba.
  - regla c): es igual
  - regla d): no se puede dar C1=C2. Habría que ver si aparece una X si
  se puede suprimir o no (por contexto)
  - regla e): si al final del mensaje descifrado aparece una X, pues ya se
  sabe que es de relleno

  ![image](https://github.com/user-attachments/assets/378b72bc-743c-4041-867c-7f0fe32c6853)
