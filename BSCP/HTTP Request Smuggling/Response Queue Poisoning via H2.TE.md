
 ---
 ![[Pasted image 20250807162341.png]]
Quan veiem H2 signifca que es un downgrade dient que el frontend interpreta HTTP 2 pero fa un downgrade a HTTP 1.1 per enviar les coses al backend


Ara no hem de canviar el HTTP a 1.1 , el podem deixar a 2
i segueix sent CL.TE. LKa diferencia esque no hem d incdicar cointent length perque el frontend ja ho calcula amb HTTP 2

![[Pasted image 20250807163104.png]]

Sense inflar el content-length doncs podem veure la solicitidu que fa el backend![[Pasted image 20250807163126.png]]

Tambe funcionaria sense utilitzar content length


## Resum visual
	
	Tu envies:
	[POST /x (amb GET smuggled dins)]
	
	El backend veu:
	→ Petició 1 (POST) → resposta 404 → torna a tu
	→ Petició 2 (GET smuggled) → resposta 302 amb sessió de l'admin → es queda a       la cua
	
	Tu tornes a connectar:
	→ El servidor et torna la resposta 302 que era per l'admin 😈


