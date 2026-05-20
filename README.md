# Espai Cràter

En aquest projecte s’analitzen les necessitats de l’Espai Cràter i les limitacions del sistema actual de pantalles interactives, amb l’objectiu de definir una solució que permeti millorar-ne el funcionament i facilitar-ne el manteniment. A partir d’aquesta anàlisi, es planteja el desenvolupament d’una nova aplicació que substitueixi l’actual sistema i permeti adaptar-lo a futures necessitats del museu.


## 📄 Documentació del projecte:

- [1.Descripció del projecte](Documentacio/1-descripcio_projecte.md)
- [2.Tecnologia](Documentacio/2-tecnologia.md)
- [3.Anàlisis de la còpia de seguretat](Documentacio/3-copia_seguretat.md)
- [4.Procés de desenvolupament](Documentacio/4-proces_desenvolupament.md)


## ⚠️ Requisits per executar el projecte

Per executar l'aplicació has de entrar al directori `AppEspaiCrater` i utiltizar la comanda `npm run tauri dev`

Perquè l’aplicació tingui els fondos de l'Espai Cràter, cal afegir manualment els vídeos utilitzats.

Aquests vídeos ***no estan inclosos al repositori*** ja que excedeixen el límit de mida de Git *(100 MB)*.

[Enllaç als vídeos](https://drive.google.com/file/d/1eVsMip8JsVvXe7s6T9YqfZJKTMkRG0yt/view?usp=sharing)

Col·loca els fitxers dins la carpeta: `AppEspaiCrater\src\lib\videos`  
Haurien de ser els vídeos:
- `background_garrotxa.mp4`
- `background_terra.mp4`
- `background_volca.mp4`

L’estructura ha de respectar els noms esperats per l’aplicació, ja que es carreguen des de rutes fixes.