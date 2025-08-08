
---
![[Pasted image 20250807004100.png]]

Hem de smugglejar una solicitud que truqui a /admin i borri a carlos

De moment tenim aixo
![[Pasted image 20250807004225.png]]

Volem que el backend interpreti chunks

La logica seria la seguent
![[Pasted image 20250807004314.png]]
El frontend veu que estem enviant 33 bytes de dades, el backend veu tot i diu perfecte, tinc el 0 i diu **final del chunk**, llavors veu qe li han enviat tambe una peticio a Get /admin, aixi qeu la executa
i si li donem a send dues vegades:
![[Pasted image 20250807004449.png]]


Pero veiem que nomes es pot per localhost, aixi que hem de cnaivar coses
![[Pasted image 20250807004844.png]]
posem un content legnth aqui mes gran que el real (test=test son 9 bytes), per a que el backend es quedi esperant a una altra peticio