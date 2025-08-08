
---
![[Pasted image 20250807160553.png]]
tenim un  CL.TE
Hem de pillar la cookie d'una victima, es a dir, agafar les capçcaleres de Cookie de la peticio que fagi l'usuari

El vector d'atac sera pels comentaris:
![[Pasted image 20250807160838.png]]

aixi que posem els transfer encoding, i posaerm com a request smuggleada una peticio sencera del que seria posar un comentari
![[Pasted image 20250807160943.png]]
Treurem totes les capçaleres menys content-type contentlength i les dades per post
![[Pasted image 20250807161014.png]]
**També hem de posar la cookie!!!!**
D aquesta manera el backend pujara un comentari amb dades noves dins del comentari de la seguent peticio ( si inflemm el content length)
![[Pasted image 20250807161305.png]]

Basicament hem de inflar molt el content lenght per que quan algu fagi una peticio dons entri dins del body

el que farem es inflar molt el content length i posar el valor de "comment" al final de tot
![[Pasted image 20250807161445.png]]
, de manera que tot el que vagi despres de coommetn sera la peticio seguent, i ho podrem veure dins del comentari

![[Pasted image 20250807161525.png]]veiem que no veiem tot sencer, necessitariem veure mes bytes, aixi que inflem mes el content length
![[Pasted image 20250807161710.png]]