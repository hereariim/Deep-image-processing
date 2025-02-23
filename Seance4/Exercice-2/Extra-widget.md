
## GUI for widget

Il existe de nombreuses bibliothèques conçues pour créer une interface graphique (GUI), comme Tkinter ou PyQt5. Sur napari, PyQt5 est fortement recommandé pour la création d'une interface graphique. Ce conseil s'adresse généralement aux programmeurs avancés. La création d'une interface graphique demande beaucoup de temps et de code. Par conséquent, il est très difficile pour les programmeurs novices de concevoir un code à partir de zéro.

### Magicgui

La communauté napari a créé la bibliothèque **magicgui** pour simplifier le processus de création d'une interface graphique. **magicgui** est une couche d'abstraction générale sur les outils de création d'interfaces graphiques (comme Qt), mettant l'accent sur la correspondance entre les types Python et les widgets. Cette bibliothèque est destinée aux programmeurs novices. Elle facilite la création de widgets pour représenter les entrées de fonction. Voici une illustration de l'utilisation de **magicgui** :

#### Quick List of magicgui parameters

- `layout` (`str`, `optionnel`) – Type de disposition à utiliser. Doit être `horizontal` ou `vertical`, par défaut `"vertical"`.  

- `call_button` (`bool` ou `str`, `optionnel`) – Si `True`, crée un bouton supplémentaire qui appelle la fonction originale lorsqu'il est cliqué. Si une `str` est fournie, elle définit le texte du bouton. Si `None` (valeur par défaut), il est défini sur `True` lorsque `auto_call` est `False`, et sur `False` autrement.  

- `result_widget` (`bool`, `optionnel`) – Indique s'il faut afficher un widget LineEdit pour afficher la sortie de la fonction lorsqu'elle est appelée, par défaut `False`.  

- **param_options** (`dict[str, dict]`) – Tout argument supplémentaire sera utilisé comme option spécifique à un paramètre. Les clés doivent correspondre aux noms des arguments de la signature de la fonction, et la valeur doit être un dictionnaire d'arguments à passer au constructeur du widget.

D'autres paramètres dans [magicgui page](https://pyapp-kit.github.io/magicgui/api/magic_factory/)

## Example

```
from magicgui import magic_factory
import datetime
import pathlib

@magic_factory(
    call_button="Calculate", # call_button
    slider_float={"widget_type": "FloatSlider", 'max': 10}, # param_options
    dropdown={"choices": ['first', 'second', 'third']}, # param_options
)
def widget_demo(
    maybe: bool,
    some_int: int,
    spin_float=3.14159,
    slider_float=4.5,
    string="Text goes here",
    dropdown='first',
    date=datetime.datetime.now(),
    filename=pathlib.Path('/some/path.ext')
):
    ...

widget_demo.show()
```

![Alt text](credit-image/7586a2670f0eb26111339c8f0fe6f8c4651ee9a9f444584181967deeb4301c80.png)

## Input et Output d'un widget

Napari identifie chaque élément selon sa classe.

### Input

Les éléments fournis par un utilisateur sont généralement considérés comme appartenant aux objets de la classe `napari.types`. Dans cette session, les utilisateurs téléchargeront des images RGB. Ces images sont représentées sous la variable `napari.types.ImageData`.  

- `napari.types.ImageData` : Images RGB  

De manière plus générale, les utilisateurs peuvent fournir des entrées pour d'autres types d'objets. Voici les types d'objets et leurs variables correspondantes :  

- `napari.types.LabelsData` : Masque d'instances  
- `napari.types.PointsData` : Données de points  
- `napari.types.ShapesData` : Données de formes  
- `napari.types.VectorsData` : Données de vecteurs

Plus d'information dans [napari.types](https://napari.org/stable/api/napari.types.html)

### Output

Les résultats des traitements dans napari sont généralement rendus sous forme de **couche** (**layer**). Ces couches appartiennent à la classe `napari.layers`. Dans cette session, les utilisateurs créeront des images binaires. Ainsi, les images binaires générées par napari sont représentées sous la variable `napari.layers.LabelsData`.  

- `napari.layers.Labels` : Masque binaire ou multi-classes  

Cet objet possède plusieurs paramètres qui fournissent des informations sur la couche. Certains d'entre eux sont listés ci-dessous :  

- `data` : Tableau ou liste de tableaux  
- `colormap` : Nom de la colormap  
- `name` : Nom de la couche

Voir [napari.layers.Image](https://napari.org/stable/api/napari.layers.Image.html#napari.layers.Image) pour une liste exhaustive de paramètres.

De manière plus générale, les utilisateurs peuvent fournir des entrées pour d'autres objets. Voici les types d'objets et leurs variables correspondantes :  

- `napari.layers.Image` : Image (peut inclure des masques binaires)  
- `napari.layers.Points` : Données de points  
- `napari.layers.Shapes` : Données de formes  
- `napari.layers.Surface` : Données de surface  
- `napari.layers.Vectors` : Données de vecteurs  

À noter que `napari.layers.Image` représente généralement des images en niveaux de gris ou en couleur, tandis que les masques binaires sont souvent mieux représentés avec `napari.layers.Labels`.
