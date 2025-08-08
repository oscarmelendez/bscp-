
---
![[Pasted image 20250808151322.png]]

---

## 🧨 Objectiu

**Fer que el fitxer `tracking.js` del lloc víctima redireccioni cap al teu servidor (`/post`)**, on tens una càrrega útil (`alert(document.cookie)`), mitjançant **Request Smuggling** i enverinament de la memòria cau (cache poisoning).

---

El frontend contempla CONTENT  LENGTH

Per resoldre el lab hem de fer un REQUEST SMUGGLING ATTACK que fagi que la cache estigui 'poisoned', de manera que la cache fagi un alert(document.cookie)


Es a dir, hem de fer que el backedn fagi una crida al nostre exploit server (on tenim un alert cookie) i veure la cookie

Quan entrem al lab veiem que es fan aquestes peticions directament
![[Pasted image 20250808151735.png]]
Ens interesen els arxius javascript com el de tracking.js![[Pasted image 20250808151803.png]]

LA respota d aquest arxiu es la seguent
![[Pasted image 20250808151816.png]]

Com veiem te una cache de 30 segons

---

Sabem que el frotend contempla Content Length, pero del backedn no ho sabem aixi que anema a provar
![[Pasted image 20250808152014.png]]
Veiem el not found
![[Pasted image 20250808152105.png]]
Aixi que ja sabem que el backend interpreta Transfer Encoding



Veiem ara que hi ha un boto que ens porta al seguent post, "Next Post", d emanera que podria ser un Open Redirect
![[Pasted image 20250808152341.png]]
I veiem que funciona perfectament![[Pasted image 20250808152358.png]]

Podem fins i tot canvia el host
![[Pasted image 20250808152529.png]]
![[Pasted image 20250808152536.png]]
Ara simplement li hem de canviar el nom al arxiu del nostre exploit server a post ![[Pasted image 20250808152601.png]]

I posarho com a host
![[Pasted image 20250808152921.png]]
## 🧪 PAS 3: Trigar el cache

Ara envia aquesta petició per fer que el sistema accedeixi a `tracking.js`:

`GET /resources/js/tracking.js HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Connection: close`




**El backend processa la smuggled request com si fos part d’una nova petició, i la resposta d’aquesta s’assigna incorrectament a la següent petició que rebi el proxy**, enverinant la cache o trencant la lògica HTTP.