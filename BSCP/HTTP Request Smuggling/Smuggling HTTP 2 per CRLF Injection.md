
----

CRLF significa retorn de carro i LF Line Feed, basicamernt **\r\n**



Primer de tot canviem la solicitud a POST, i posem HTTP 2 (ja ho estava)

i provem amb Transfer Encoding

Pero veiem que no passa res
![[Pasted image 20250807210629.png]]

en aquests casos em de posar el Transfer Encoding dins d'una altra capçalera
![[Pasted image 20250807210802.png]]


d'aquesta manera si que funciona
![[Pasted image 20250807210903.png]]


El que farem ara es aixo
![[Pasted image 20250807211009.png]]
On al posarli tants bytes a content length. el que sigui que es busqui, se li sumara les peticions que segueixin fins a arribar als 850 bytes, donant-nos aixi alguna cookie o informacio important

![[Pasted image 20250807211143.png]]
