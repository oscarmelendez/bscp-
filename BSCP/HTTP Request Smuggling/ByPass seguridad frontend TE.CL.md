
---

Tenim aixo
![[Pasted image 20250807013029.png]]

Hem de posar ara una mida al content lenght per que el backend ho llegeixi
![[Pasted image 20250807013146.png]]
El **content length** de la linia 9 es el que hem d incorporar, realment son 19 bytes pero li posarem una mica més --> 22 bytes

El  **size** de la linia 6 seria tot això, és a dir, 48 (HEX)
![[Pasted image 20250807013306.png]]

i el primer content lenght serà 4, perque volem qeu llegeixi just abans de la linia 7
![[Pasted image 20250807013407.png]]
es a dir uqe nomes llegeixi el 48 el backend. i tot lo de despres ho interpreti com a una altra solicitud

Simplement amb aixo ja estaria, si no va be doncs hem de posar més bytes dins del content lenght de la peticio smuggleada
