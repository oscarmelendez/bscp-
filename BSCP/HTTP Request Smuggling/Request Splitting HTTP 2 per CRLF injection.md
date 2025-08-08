
---

![[Pasted image 20250807212220.png]]

Aqui el frontend mira Content Length, i el backend Transfer Encoding
![[Pasted image 20250807212407.png]]

Tenim això, anem a treure-li les capçaleres que no necessitem
![[Pasted image 20250807212540.png]]
Veiem que aixo no dona cap error, cosa que es extranya, aixi que anem a 'colar' la part del Transfer Encoding dins d'una altra capçalera
![[Pasted image 20250807212643.png]]

Per fer el enter aquest amb \r \n doncs fem "SHIFT + ENTER"

D'aquesta manera tampoc  ens retorna algo


---

<h1>Provem a canviar la request a GET</h1>

---


Aixi que provarem de canviar una altra capçalera![[Pasted image 20250807212850.png]]

I aqui si que rebem el 404
![[Pasted image 20250807213123.png]]


Ara el que hem de fer es capturar el inici de sessio de la victima, per tal de que a ell li surti el "NOT FOUND" quan inicïi sessió i a nosalrtesel 302 Found amb la seva cookie

![[Pasted image 20250807213344.png]]

