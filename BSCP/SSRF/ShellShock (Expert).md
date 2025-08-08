
---
![[Pasted image 20250806224958.png]]


Hem d'anar iterant el ultim octet de la IP i anar veient fins que trobem la correcta

sabem que la web fa una solicitud a la URL que hi ha al REferer, per tant posarem la nostra (Burp Collaborator's) per que ens fagi una petició a nostaltres
![[Pasted image 20250806225129.png]]
![[Pasted image 20250806225145.png]]

El shellshock es aixi:
![[Pasted image 20250806225300.png]]

L'atac seria alguna cosa així ![[Pasted image 20250806225427.png]]


Per tant a part d axio el referer ha de ser la ip correcta, aixi que anem a ferho amb el intruder ![[Pasted image 20250806225454.png]]

El quie fara es, si el referer existeix, el user-agent s executara, per tant la comanda de nslookup amb wl valor de whoami funcionara quan trobem la IP