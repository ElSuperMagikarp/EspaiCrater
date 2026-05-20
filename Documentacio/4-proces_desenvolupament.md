# Procés de desenvolupament
Explicació del procés que he seguit per desenvolupar l’aplicació i les decisions que he pres durant el desenvolupament.


## Extracció d’assets
Si vull que l’aplicació sigui com l’existent, m’és indispensable la utilització de les imatges i animacions, ja que són una gran part de l’apartat visual de les pantalles de l’Espai Cràter.

Desafortunadament, els assets que he aconseguit a la còpia de seguretat són escassos, i sembla que els treballadors de l'Espai Cràter tampoc els tenen. Ara mateix, l’única manera possible que veig per obtenir els assets és extraient-los directament dels executables. Amb l’ajuda de [Asset Studio](https://github.com/Perfare/AssetStudio), una eina de codi obert externa que és capaç d’extreure assets d’un executable de Unity, he sigut capaç d’indagar en els assets del projecte.

En buscar els assets dels projectes, m’he trobat que les animacions que hi ha estan guardades de manera bastant peculiar. No són `.mp4` o `.gif` com jo pensava que serien, sinó que està importat cada fotograma de l'animació com a Sprite individual, i després es construeix l’animació utilitzant el sistema d’animacions de Unity. Això complica bastant l’extracció de les animacions, ja que implica que, per cada animació, s’ha d’extreure cada fotograma individual i posteriorment unificar-los en el format que es necessiti.

## Estudi de components
Si vull construir una base sòlida en la qual després sigui fàcil desenvolupar la resta de l’aplicació, considero important crear components que siguin reutilitzables per tota l’aplicació.

El problema és que com la guia d’estils és bastant pobre i no tinc a ningú que sàpiga com es va fer a l’aplicació perquè m’ajudi, no sé quins components em fan falta per fer l’aplicació.

Per poder aconseguir tot això sense ajuda, he considerat que el millor és fer un estudi de l’aplicació, anant pantalla per pantalla i anotant els elements que veig que es repeteixen conjuntament amb la seva funció, comportament, possibles variants, i tot el que consideri necessari.

Per fer aquesta feina he decidit documentar-ho amb l’eina **Notion**. L'estudi de components està guardat a dins el directori **Recursos Varis**, on trobareu un `.zip` que es pot importar a Notion.