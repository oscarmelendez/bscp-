
---
![[Pasted image 20250806224249.png]]
En aquest LAB hem de fer que el Stock Check URL canvii i accedeixi a http://192.168.0.12:8080/admin i eliminar el user 'carlos'


Veiem que tenim aixo 
![[Pasted image 20250806224401.png]]


Veiem ara que hi ha un botó de 'Next Product'
![[Pasted image 20250806224539.png]]

en el qual si nosaltres cliquem
![[Pasted image 20250806224603.png]]
On la variable 'path' es pot canviar per una URL:
![[Pasted image 20250806224630.png]]
Per tant tenim un *Open Redirect*


Ara simplement ho posem dins del burpsuite

![[Pasted image 20250806224704.png]]![[Pasted image 20250806224751.png]]


Mirem el codi de la resposta i per borrar es aquí:
![[Pasted image 20250806224846.png]]