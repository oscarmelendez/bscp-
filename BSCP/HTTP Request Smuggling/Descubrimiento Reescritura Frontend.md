
---

![[Pasted image 20250807155104.png]]

Hem de fer una peticio a dins de /admin. que no es accesible per la gent de fora (frontend)
I hem de borrar l'usuari "carlos"

estem en un CL.TE

i la part vulnerable es troba a la funcio de "search"
![[Pasted image 20250807155227.png]]

Ara hem de posar-ho com a HTTP Request Smuggling, es a dir, posem HTTP 1.1 i borrem totes les capçaleres
![[Pasted image 20250807155338.png]]

A partir d aqui posem el transfer encoding per enviar la peticio

Podem comprovar que funciona de la seguent manera
![[Pasted image 20250807155444.png]]
a content length nomes ens llegira fins la linia '8' (incluida), pero no el 0, per tant nomes enviar "3 abc" al backend, i  el backend es quedara esperant el 0 per tancar el chunk, aixique tindrem un timeout error
![[Pasted image 20250807155536.png]]
Aixi que ara anem a posar la solicitud nova
![[Pasted image 20250807155646.png]]
aqui tots els bytes de content length son els reals, no estem inflant res


Pero si li inflem els bytes de dins de la solicitud que volem colar
![[Pasted image 20250807155756.png]]
si que ens funcionara i ens fara una solicitud per post amb search=test
![[Pasted image 20250807155823.png]]
com podem veure ens posa tambe 'PO', que es la part de la seguent solicitud que el backend mescla amb la que nosaltres hem smugglejat

Si posessim mes content length doncs veuriem mes info
![[Pasted image 20250807155932.png]]
Per borrar l usuari necessitem la capçcalera aquesta per tant 
![[Pasted image 20250807160129.png]]
