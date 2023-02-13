# FreeCAD Project Bootstrap

Télécharger ou cloner ce repository pour démarrer un nouveau projet FreeCAD.

Ce projet FreeCAD se veut réparti sur plusieurs fichiers et doit utiliser les
[liens](https://wiki.freecad.org/Std_LinkMake) pour reliers ces fichiers entre
eux.

## Arch

- `model/` : objets 3D (.FCStd), i.e. pièces et assemblages.
    - `.` : placer ici le top-level assembly
    - `GlobalVars.FCStd` : contient les variables globales du projet
    - `parts/` : contient les differentes pièces du projet (generalement groupées
par dossier).
- `techdraws/` : projections sur plans (.FCStd). Sert à générer des `.pdf` et
`.dxf`.
Généralement, le nom des fichiers techdraws sont le nom de la pièce qu'ils
illustrent, avec le suffix `TD`, e.g. `PlateTD.FCStd`.
- `exports/` : créer ici un dossier contenant le nom du projet
et y fournir les `.stepZ`, `.dxf` et `.pdf` des pièces du projet (regroupés dans
un même dossier par pièce). Ce dossier sera à distribuer.
    - `Commande.FCStd` : sert à générer un .csv contenant la commande à envoyer
au client ou au lazeriste (donc à placer dans le dossier à distribuer).

Le nouveau dossier `exports/<project_name>/` peut être distribué sous forme
d'archive via la commande suivante une fois que son contenu a été commit :

```bash
$ cd exports/

$ git archive -o ~/<output_file_name>.zip HEAD <project_name_dir>/
```
