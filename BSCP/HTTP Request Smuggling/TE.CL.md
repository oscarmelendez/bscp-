
---

Aqui hem de fer el mateix, que el backend fagi una peticio amb un GPOST

![[Pasted image 20250807220756.png]]

El frontend contempla Transfer Encoding, aixi que aqui hem de fer primer un transfer Encoding
![[Pasted image 20250807220933.png]]

Seria fer aixo, on 'size' es la mida del qeu hia ha subrallat, i el content lenght que tenim a sota esta una mica inflat


El backend dirà:
![[Pasted image 20250807221033.png]]
Vale, content length de **4**, llavors interpreto el numero 72, perod despres justament veu una peticio amb elk metode **GPOST**![[Pasted image 20250807221139.png]]