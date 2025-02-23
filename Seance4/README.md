# Napari

Napari est disponible sous deux formes
- Logiciel : **Bundled app**
- Librairie python : **Python package**

## Installation via Python package

Dans votre console conda, créer un environnement virtuel napari-env: 

```
conda create -y -n napari-env -c conda-forge python=3.9
conda activate napari-env
```

Dans l'environnement nouvellement crée, installer napari :

```
python -m pip install "napari[all]"
```

Note: Lancer `pip install "napari[all]"` installe napari avec le framework par défaut PyQt5 utile pour l'interface utilisateur. Lorsque l'installation est terminée, lancer napari avec la commande suivante : 

```
napari
```

![Alt text](credit-image/napari_launched.png)

I refer you to this [page](https://napari.org/stable/tutorials/fundamentals/installation.html#install-as-python-package-recommended) for more information.