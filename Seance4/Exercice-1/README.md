# Exercice 1 : Créer un plugin simple

# Requirements

Dirigez-vous dans l'environnement conda :

```bash
conda activate napari-env
```

# Créer un plugin

Tout d'abord, nous allons créer un répertoire contenant la structure du plugin. L'outil copier permet de créer une structure simple du plugin. 

Installer copier :

```bash
python -m pip install copier jinja2-time
python -m pip install npe2
```

Une fois installer, créer le répertoire avec la commande :

```bash
copier copy --trust https://github.com/napari/napari-plugin-template napari-seg
```

Informations à remplir :

```bash
🎤 The name of your plugin
   napari-seg
🎤 Display name for your plugin
   Segmentation
🎤 Plugin module name
   napari_seg
🎤 Short description of what your plugin does
   Segmentation images
🎤 Email address
   bob@gmail.com
🎤 Developer name
   Bob
🎤 Github user or organisation name
   bob
🎤 Github repository URL
   provide later
🎤 Include reader plugin?
   No
🎤 Include writer plugin?
   No
🎤 Include sample data plugin?
   No
🎤 Include widget plugin?
   Yes
🎤 Use git tags for versioning?
   No
🎤 Install pre-commit? (Code formatting checks)
   No
🎤 Install dependabot? (Automatic security updates of dependency versions)
   No
🎤 Which licence do you want your plugin code to have?
   BSD-3
```

Vous venez de créer un plugin napari avec une structure simple :

```bash
napari-seg/
│
├── .github
│   └── workflows
│      └── test_and_deploy.yml
├── LICENSE
├── MANIFEST.in
├── napari_seg
│   ├── __init__.py
│   ├── _widget.py
│   ├── napari.yaml
│   └── _tests
│       ├── __init__.py
│       └── test_widget.py
├── pyproject.toml
├── README.md
├── setup.cfg
└── tox.ini
```

Une fois le répertoire créer, dans la console, dirigez-vous dans le répertoire puis lancer l'installation :

```bash
pip install -e . #Install plugin locally
```

Lancer `pip install -e .` où  `pyproject.toml` est situé

⚠️ *Note: Vous installez le plugin en tant que librairie python. Il n'apparaitra pas dans le logiciel napari, ce qui nécessiterais un déploiement du plugin que nous ne verrons pas dans ce cours.*
