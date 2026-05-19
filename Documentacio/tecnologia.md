# Tecnologia
Anàlisis de la tecnologia que es va utilitzar per fer l'Espai Cràter, i quina hauria d'utilitzar per fer-ho de nou.


## Tecnologia antiga

La tecnologia que es va utilitzar per fer el programa de les pantalles va ser Unity.

Cada pantalla té un executable diferent, la qual cosa implica que hi havia un projecte de Unity per cada una de les pantalles.

En la següent secció explico amb profunditat la meva opinió sobre la utilització de Unity en aquest projecte, així que no detallaré gaire, però diré que no em sembla per res bona opció.


## Anàlisi de tecnologies

He analitzat múltiples tecnologies per considerar quina és l'adequada per fer el nou projecte. Tot seguit exposo els seus punts forts i febles segons el meu punt de vista:

### Unity
Unity, la qual va ser la tecnologia escollida anteriorment, no crec que sigui adequat. Encara que, investigant una mica, he trobat que s’utilitza a l’hora de desenvolupar software per museus, no em sembla una bona tecnologia per aquesta tasca.

Per començar, que cada pantalla sigui un projecte de Unity diferent resulta molt poc òptim. Això implica codi i assets duplicats en pràcticament cada pantalla, ja que totes les pantalles tenen la mateixa estètica i hi ha elements que es repeteixen moltíssim. Si ho fes d'aquesta manera segurament es convertiria amb una odissea fer el manteniment del museu.

Després, tan senzilles que són les pantalles del museu, Unity no és bona opció per això. Unity és un motor pensat per fer videojocs i la part de UI és bastant pesada de fer, sobretot els menús. Tenint en compte que les pantalles són en gran majoria menús i no tenen massa interactivitat, Unity resulta una opció poc adequada.

Addicionalment, Unity no té una manera d'estilitzar els elements (i si en té, és molt bàsica), el que vol dir que per poder aconseguir que els menús quedin estèticament macos es requereix la utilització de assets (majoritàriament imatges) per poder-ho fer tot.

L’únic avantatge que li veig al Unity és la connectivitat amb el hardware, ja que bastants pantalles tenen un hardware extern el qual interactua amb la pantalla de diferents maneres. En aquest sentit, Unity simplifica bastant la comunicació amb aquest hardware per la interactivitat, però això no és una raó amb prou pes per a escollir aquesta tecnologia.

### Web (HTML/CSS)
Fer-ho amb una web considero que pot ser una bona opció, ja que és una tecnologia pensada per ensenyar informació i navegació de menús, però té alguns problemes.

Començant pels avantatges, HTML/CSS és una tecnologia creada per fer interfícies d’usuari, per tant, hauria de ser capaç de recrear tota la part gràfica de les pantalles.

Les coses que no es podrien fer en HTML i CSS, principalment les parts interactives, es poden fer amb JavaScript, el qual no crec que sigui massa complicat, ja que la majoria de les coses interactives són bastant senzilles.

Entrant amb els desavantatges, la raó principal que em fa evitar és la connectivitat amb el hardware. Una web no està instal·lada al sistema operatiu, per tant, no és capaç d’accedir als outputs d’aquests hardwares. Per poder fer que el hardware interactuï amb la pàgina s’hauria de muntar un sistema que li enviï les dades a la web perquè reaccioni, però és sobre-complicar-ho massa i segurament afectarà el rendiment (ja que hi haurà un retard segurament bastant notable).
Ara mateix això no m’importaria gaire, pel fet que és possible que no arribi a fer una pantalla que tingui hardware, però en el futur pot ser un problema molt gros que no tingui una bona solució, el que m’ha portat a descartar la tecnologia.

Una altra raó que no té tant de pes, però s’hauria de considerar és que una web en navegador em fa por que sigui massa fràgil per un museu, ja que deixa unes llibertats que no haurien de tenir les pantalles. Per exemple, que els usuaris siguin capaços de treure la pantalla completa, o obrir l’inspector. Això són ja casos una mica extrems, però podrien passar i depenen del navegador, el qual és un software que no podem modificar.

### React Native
React Native no em sembla una mala opció per fer el projecte, ja que és similar a web, però es pot instal·lar com a aplicació nativa. El problema que hi tinc és que personalment no m’agrada. A una assignatura del cicle vam treballar amb React tot l’any, i hi ha coses que estan molt bé, però hi ha coses que no m’agraden gens.

El projecte es podria fer perfectament en React, però per preferència personal i males experiències, vull evitar-ho.

### Tauri
Investigant quines tecnologies podria utilitzar, em vaig trobar amb Tauri. En resum, Tauri és un framework que et permet fer una aplicació web i poder-la convertir a una aplicació nativa d'escriptori, això ho aconsegueix fent servir un back-end amb Rust.

Tauri soluciona tots els problemes que tenia amb fer una aplicació web. Em deixa utilitzar HTML/CSS, d’aquesta manera puc treballar amb una tecnologia coneguda, i soluciona els problemes que porten el navegador. Gràcies al seu back-end amb Rust, Tauri és capaç de comunicar-se amb el hardware per poder influenciar l'HTML sense processos complicats.


## Tecnologia escollida
La tecnologia que he escollit pel projecte és **Tauri**. Tauri em deixa treballar amb HTML/CSS, la qual és una tecnologia en què hi tinc experiència, i soluciona tots els problemes que tenia amb HTML/CSS.
En teoria hauria de poder llegir el hardware de l'espai cràter i tenir control total de l'aplicació sense dependre de funcionalitats no desitjades dels navegadors.

A part de Tauri, també he escollit algunes tecnologies adicionals que funcionen sobre Tauri que m’ajudarán a treballar millor:

### Tailwind
Un framework de CSS (Com Bootstrap) que agilitza molt el procés de posar estils a l’aplicació. L’he escollit perquè és molt còmode, i ja hi tinc experiència.

### Svelte
Svelte és un framework que dona moltes facilitats a l’hora de fer la web. Et deixa fer coses com utilitzar variables dintre l’HTML i t’ajuda a estructurar la web gràcies a components i layouts dinàmics.