# Tema 1: Criptología

# ALGORITMOS DE SUBSTITUCIÓN

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


  a. Si m_1,m_2 na misma fila -> C_1,C_2 son os dous caracteres da dereita. Exemplo: ft -> LZ
 
  
  b. Si m_1,m_2 na misma columna -> C_1,C_2 son os caracteres de abaixo


  c. Si m_1,m_2 en filas/columnas distintas -> C_1,C_2 son os caracteres da diagonal desde m_1

  
  d. Si m_1=m_2 añádese un separador (normalmente unha X)


  e. Si o número de carácteres é impar, añadese un caracter final (normalmente unha X) 

 
O descifrado aplica as mismas reglas que o descifrado pero:
  - regla a): en lugar de sustituir por los caracteres de la derecha, se sustituyen por los de la izquierda, y
  - regla b): en lugar de sustituir por los caracteres de abajo, se sustituyen por los de arriba.
  - regla c): es igual
  - regla d): no se puede dar C1=C2. Habría que ver si aparece una X si
  se puede suprimir o no (por contexto)
  - regla e): si al final del mensaje descifrado aparece una X, pues ya se
  sabe que es de relleno

  ![image](https://github.com/user-attachments/assets/378b72bc-743c-4041-867c-7f0fe32c6853)

## Vigenère

É un cifrado por **substitución polialfabeto** Usa diferentes series de cifrado César, basándose en letras dunha palabra clave.

![image](https://github.com/user-attachments/assets/4f9b8466-f073-42b4-8d2c-99eebfd9bd69)

![image](https://github.com/user-attachments/assets/a79ddee0-7c5c-485a-9605-6be1d50c22c6)

![image](https://github.com/user-attachments/assets/879fcf99-4fdd-4221-950b-374dec142f48)

Ao utilizar diferentes alfabetos destruimos a relación nas frecuencias de aparición que tiñan os monoalfabetos.
Resistiu casi 300 anos de criptoanálisis polo que se chamou **a cifra indescifrable**

Existen variantes do cifrado Vigenère:
- Autoclave
- Vernam
- 


### Autoclave

Variante que unha vez chegase a última letra da clave continúase usando como clave do propio mensaxe
![image](https://github.com/user-attachments/assets/e05abe53-8ef1-4e3d-90bd-b4940d852ded)

### Vernam

Propón usar unha clave aleatorio moi larga, con repetición. Funciona con bits en vez de letras (usabase no telegrafo e codificaba en 5 bit)
Sigue o esquema chamado **cifrador de fluxo**.
Para cifrar utiliza a función exor entre o mensaxe e unha clave, e para descifrar fai exor entre o mensaxe codificado e unha copia da clave.

![image](https://github.com/user-attachments/assets/ae657c78-cda0-4fab-9e87-73c6e8e4ebdf)

### One-Time Pad (OTP)

É unha mellora ao Vernam. Ten como peculiaridad que a clave é aleatoria e debe ser tan larga como o mensaxe, para non repetirse. Ademais, a clave usase para cifrar e descifrar unha sola vez; despois descartase.

**É un esquema irrompible** (*perfect secrecy*) xa que a súa salida non se relaciona co texto (equiprobabilidad, igualdad de tamaño entre mensaxe-alfabeto-codificación). A verdadeira seguridad reside na aleatoriedad da clave; aínda que, na práctica, é problemática esa xeneración de claves grandes

# ALGORITMOS DE TRANSPOSICIÓN

## Edad precientífica pt2
### Escítala (Scytale)

Mecanismo de cifrado que data do V a.C. Bastón en el que se enrollaba una cinta de cuero y luego se escribía
en ella el mensaje de forma longitudinal
 Para descifrar el criptograma y recuperar el mensaje en claro habrá
que enrollar dicha cinta en un bastón con el mismo diámetro que el
usado en el extremo emisor y leer el mensaje de forma longitudinal
 La clave del sistema se encuentra en el diámetro del bastón
 Cifrado por transposición

### Rail Fence (zigzag cipher)

Básase na escritura dunha M en ZigZag (distintas profundidades)
El número de filas es la clave
Lectura de M fila a fila
Cifrado de transposición

![image](https://github.com/user-attachments/assets/022120a9-fd8b-4fbc-bb51-8f3cd32da8e4)

### Transposición de columnas

Escritura de M en un rectángulo, fila por fila y leer el mensaje
columna por columna, pero permutando el orden de las columnas
 El orden de las columnas es la clave
 Cifrado de transposición

![image](https://github.com/user-attachments/assets/ae5a00d0-c767-4206-9a86-0ec0fc1aa9cc)

# Cifrado Simétrico

## RC4

## DES

### 3DES

## AES

# Cifrado Asimétrico

Basase no uso de dúas claves, unha clave pública e unha clave privada. A clave pública distribúese para o descifrado e a privada non. Debe ser inviable descifrar ca misma clave ca que se descifrou, descifrase ca inversa. De esta forma podemos conseguir aportar confidencialidad (si se cifra ca pública solo pode descifrar o que teña a privada do emisor) ou autenticación (o que cifre ca privada pódese descifrar ca pública, é dicir, calquera ademáis sendo el emisor inequivoco), e integridad (si o mensaje alterase, no se pode descifrar) con no repudio (firma digital, un emisor non pode negar haber cifrado un archivo ca súa clave privada)

O primeiro algoritmo de cifrado exitoso e que cumple as propiedades é RSA, desarrollado no MIT por Ron Rivest, Shamir e Adleman

## RSA

É un cifrado de bloque no que o texto claro e o texto cifrado son enteiros entre 0 e n-1 para algún n (tipicamente 1024, actualmente 2048). Básase na exponenciación e consiste en:

- Seleccionar dous numeros primos grandes p e q
- Calculase n=p-q
- Calculase fi(n)=(p-1)(q-1)
- Seleccionase a clave e tal que 1 < e < fi(n), mcd(e,fi(n))=1
- Obtener clave de descifrado d (co algoritmo de Euclides extendido):  e-d=1mod fi(n) y 0 <= d <= n
- Clave publica : PU={e,n}
- Clave Privada : PR={d,n}
- DESTRUIR os numeros intermedios

**COMO CIFRA**

Texto plano M dividese en bloques de representación decimal < n (Si n = 187 o max sería -> 1011 1010 polo que con 8 bits non poderíamos collelos poderíamos pasasrno, habería que usar 7 bits)
Fariamos M ^ e mod n

**COMO DESCIFRA**

Texto cifrado dividese en C bloques < n como antes.
Fariamos C ^ d mod n

## Diffie-Hellman

Supón o mecanismo de intercambio de claves que se utiliza no cifrado asimétrico por un canal inseguro. Basase en logaritmos discretos, e a clave calculada pode usarse para despos cifrar os mensajes.
