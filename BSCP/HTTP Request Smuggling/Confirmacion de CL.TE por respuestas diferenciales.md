
---

Què és 'CL.TE' --> Content Length. Transfer Encoding
Es a dir, el frontend interpreta **Content Length** i el backend interpreta **Transfer Encoding**

![[Pasted image 20250806235829.png]]

Tenim que el frontend no sporta chunked encoding

Per fer el LAB, hem de smugglejar una HTTP Request al Backend per a que quan fem una peticio a /, surti error 404

![[Pasted image 20250807000004.png]]

Hi ha dos encabezados, Content-Length i Transfer Encoding
![[Pasted image 20250807000049.png]]
a la part de transfere encoding s'indica el "size" en bytes en HEXADECIMAL (3)
La segona fila seria els bytes de dades reals
I abaix es posa el final del 'chunk', sempre es un 0


El risc d'aixo es que podem fer bypass certs mecanismes del frontend per posar coses al backend

---
<h1>LAB</h1>

Primer de tot canviarem el http/2 a http/1.1
![[Pasted image 20250807000601.png]]![[Pasted image 20250807000607.png]]

Borrarem tota les cabeceras nomes deicant content lenght
![[Pasted image 20250807000651.png]]
I li donarem a aquesta opcio, per poder anar modificant nosaltres el Content Length com vulguem
![[Pasted image 20250807000721.png]]
Hem d'activar tambe la part de \n per poder veure els salts de linia
![[Pasted image 20250807000941.png]]

El que hem de fer es posar les dades com a transfer encoding Chunked, i deixar el content lenght, a aprtir d'aqui començarem a toar coses
![[Pasted image 20250807001200.png]]
En aquest cas, el frontend llegirà els 9 primers bytes (4 abcd), ignorant el ultim '0'. 
De manera que el backend rep tot aixo (nomes lo subratllat):
![[Pasted image 20250807001408.png]]
 I es queda esperant a que li enviin el '0' (que es el simbol de que s acaba aixi les dades)

Per arribar al ERROR 404, d'afegir una nova solicutid, dientli que volem fer un get a una ruta que no existeix
![[Pasted image 20250807001815.png]]

En aquet cas tot lo subrallat son 41 bytes (conten length), el frontend ho envia com a dades (no interpreta la solicitud)
El backend el que fa és llegir tot, diu 3 bytes, 'abc', veu el '0' i diu perfecte, ja ha acabat, pero despres veu la solicitud de GET /error i la realitza.

ara quan