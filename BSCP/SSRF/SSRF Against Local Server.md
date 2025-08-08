
---

SSRF (Server-Side Request Forgery) és un atac on un servidor és enganyat per fer peticions a recursos interns o externs que l’atacant vol accedir, explotant la confiança del servidor per comunicar-se amb altres sistemes.

En aquest lab hem d'arribar a localhost/admin per eliminar la conta de l'usuari **carlos**
![[Pasted image 20250806202048.png]]

Els ports que hi ha dins de la maquina no son accessible des de fora, (pivoting), per tant hem de fer que la maquina ens retorni aquells ports
![[Pasted image 20250806202218.png]]
Si posessim aixo, la maquina faria la peticio a ell mateix, i podriem veure aixi els serveis interns


<h1>LAB</h1>
Si anema  Check STock, i agaem la peticio per burpsuite, 
![[Pasted image 20250806202708.png]]

i depenent del que posis a la url doncs reps el stock que tinguin


SI posem llocalhost, a la resposta podem veure que hi ha un panel de admin![[Pasted image 20250806202820.png]]

![[Pasted image 20250806202855.png]]

i des d'aqui podem eliminar l usuari
![[Pasted image 20250806202950.png]]

![[Pasted image 20250806203010.png]]