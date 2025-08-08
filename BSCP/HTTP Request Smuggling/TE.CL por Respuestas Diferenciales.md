
---

Una altra vegada farem lo de HTTP 1.1 i canviarem GET a POST

Ens treiem tota els headers i posem nomes Transfer Ecnoding
![[Pasted image 20250807002535.png]]
Si indiquem el 0 veiem com funciona i ens retorna la pagina, si treiem el 0 doncs no!

El backend simplement mirara el tants bytes com el Content Length Tingui!

![[Pasted image 20250807002723.png]]
Per exemple. aqui les dades tenen **13 bytes**, pero el **Backend** està esperant **15 - (content length)**, per tant es quedara esperant 

<h1>Com colem la solicitud?</h1>

Hem de posar un Content Length mesd petti
posarem la solicuitud dins de les dades

El Size que hem de posar es justament aquest, 
![[Pasted image 20250807003220.png]]
Sense tenir en compte el  \r \n  després de la 'A'
en aquest cas **Size = 1b** (HEX)

Per tant, el que hem de fer es el seguent

![[Pasted image 20250807003455.png]]

El size de la linia 6 es de la linia 7 fins a la 10 sense comptar el \r \n, i el content legnth de la linia 8 es el que va de la linia 9 (incluida), fins la linia 12

**Primer 'size'
![[Pasted image 20250807003701.png]]
**Segon Content -Length**
![[Pasted image 20250807003639.png]]

Aqui el que hem de fer per que funcioni. li hem de posar un byte mes dins del segon content length, i ja ens retornara un error 404
![[Pasted image 20250807003805.png]]