
---
![[Pasted image 20250806222745.png]]
En aquest lab hi ha una certa dificultad en la cual hi ha un sistema de defnsa quwe preveu posar '/admin' o 'localhost'


Hem d'arribar a localhost/admin
pero ens surt que esta blocked for security reasons
![[Pasted image 20250806222915.png]]
![[Pasted image 20250806222922.png]]

Com podem referenciar localhost?
### 🔹 **Què és la xarxa 127.0.0.0/8?**

Tota la xarxa **127.0.0.0 fins a 127.255.255.255** (és a dir, **/8**) està reservada per a **loopback**, 

si diem 127.0.0.1 és localhost.
127.0.0.2 tambe es localhost

127.0.0.55 també etc etc
![[Pasted image 20250806223029.png]]
aixo tambe es localhost

127.1 tambe es localhost

Pero cap d'aquestes ens funciona...

Ho representarem en Hexadecimal
127.0.0.1 --> 0x7f000001
![[Pasted image 20250806223135.png]]



Si no funciona en Hexadecimal ho farem en decimal.

127.0.0.1 en decimal seria:
![[Pasted image 20250806223316.png]]
i tot aixo donaria:
**2130706433**
![[Pasted image 20250806223408.png]]
Veiem que tampoc funciona així;
![[Pasted image 20250806223432.png]]

El problema està en la cadena "admin"

Ja que si no el posem_
![[Pasted image 20250806223514.png]]

Podem entrrar perfectament a la web![[Pasted image 20250806223528.png]]


Doncs anem a encodear el "admin"
Anem a fer-ho DOBLE URL ENCODE
![[Pasted image 20250806223624.png]]

Primer codifiquem la "a" --> %61
i després el "%" de "%61" --> %25

![[Pasted image 20250806223708.png]]

D'aquesta manera la web quan ho descodifici nomes veura %61, perque haura defcofidcart el "%", i per tant entrarem ja al panel de admin:
![[Pasted image 20250806223744.png]]

Ara simplement fariem aixo
![[Pasted image 20250806223821.png]]

I ja estaria esborrat
