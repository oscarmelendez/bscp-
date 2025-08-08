
---
![[Pasted image 20250808145817.png]]
En aquest lab hem de tornar a aconseguir que el backend fagi una peticio amb el mètode **GPOST**

Fem el de sempre, posem HTTP 1.1 i pasem de GET a POST
![[Pasted image 20250808150049.png]]

A partir d'aqui posarem Transfer - Encoding
![[Pasted image 20250808150108.png]]

Si posem això i dona un error, sabrem que el frontend interpreta Transfer - Encoding
![[Pasted image 20250808150134.png]]
 
 <h2>Frontend  --> Transfer Encoding</h2>
 
---
**Ara anem a veure que interpreta el Backend**

![[Pasted image 20250808150250.png]]
la mida de les dades ' 3 abc', es de 13 bytes, pero li posarem 15 per veure si el backend interpreta Content Length.
Si interpreta content length, el backen llegira 3, abc i es quedara esperant per als 2 bytes restants per arribar a 15, per tant es produirà una desincronització

Veiem que la respota es sempre un ***200 OK***, per tant sabem que interpreta **Transfer Encoding** també

---

A l'enunciat ens diuen que hem de 'obfuscar' el Header de **Transfer Encoding**, una manera de fer-ho es la següent:
![[Pasted image 20250808150717.png]]

El frontned, al posar dues Headers identics, el que fa es agafar l'últim, pero veu que es invalid aixi que es queda amb el 1er (chunked)

El que pasa ara es que el backend llegeix el ultim i veu que es "invalido", per tant li es igual els altres i 'esborra' els headers de Transfer Encoding i comença a interpretar **Content Length**

Així:
![[Pasted image 20250808151124.png]]
![[Pasted image 20250808151134.png]]