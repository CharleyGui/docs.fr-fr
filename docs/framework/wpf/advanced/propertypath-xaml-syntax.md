---
title: PropertyPath, syntaxe XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 5dc8fc8c43e43691c46ad84379fe2bcb23987667
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660800"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath, syntaxe XAML

Le <xref:System.Windows.PropertyPath> objet prend en charge un ligne de complex [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe permettant de définir les propriétés qui prennent le <xref:System.Windows.PropertyPath> type comme valeur. Cette rubrique explique comment le <xref:System.Windows.PropertyPath> syntaxe comme appliquée aux syntaxes de liaison et d’animation.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Cas d’utilisation de PropertyPath

<xref:System.Windows.PropertyPath> est un objet commun utilisé dans plusieurs [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionnalités. Malgré l’utilisation courantes <xref:System.Windows.PropertyPath> pour communiquer les informations de chemin d’accès de propriété, les utilisations de chaque zone de fonctionnalité où <xref:System.Windows.PropertyPath> est utilisé comme un type varier. Par conséquent, il est plus pratique de documenter les syntaxes par fonctionnalité.

Principalement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise <xref:System.Windows.PropertyPath> pour décrire les chemins d’accès de modèle d’objet pour parcourir les propriétés d’un objet de source de données et pour décrire le chemin d’accès cible pour les animations ciblées.

Certaines propriétés de style et de modèle, telles que <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> prennent un nom de propriété qualifié qui ressemble en apparence à une <xref:System.Windows.PropertyPath>. Mais ce n’est pas un véritable <xref:System.Windows.PropertyPath>; au lieu de cela, il est qualifié *owner.property* chaîne utilisation format prenant en charge par WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur en association avec le convertisseur de type pour <xref:System.Windows.DependencyProperty>.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath pour les objets dans la liaison de données

La liaison de données est une fonctionnalité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui permet d’effectuer une liaison à la valeur cible d’une propriété de dépendance. Toutefois, la source d’une liaison de données ne doit pas nécessairement être une propriété de dépendance, elle peut être n’importe quel type de propriété reconnu par le fournisseur de données applicable. Chemins de propriété sont utilisés en particulier pour le <xref:System.Windows.Data.ObjectDataProvider>, qui est utilisé pour obtenir des sources de liaison à partir de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objets et leurs propriétés.

Liaison de données à [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] n’utilise pas <xref:System.Windows.PropertyPath>, car il n’utilise pas <xref:System.Windows.Data.Binding.Path%2A> dans le <xref:System.Windows.Data.Binding>. Au lieu de cela, vous utilisez <xref:System.Windows.Data.Binding.XPath%2A> et spécifiez la syntaxe XPath valide dans le [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] des données. <xref:System.Windows.Data.Binding.XPath%2A> est également spécifié sous forme de chaîne, mais n’est pas décrit ici. consultez [lier aux données XML à l’aide un XMLDataProvider et requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Un élément essentiel qui permet de comprendre les chemins de propriété dans la liaison de données est que vous pouvez cibler la liaison à une valeur de propriété individuelle, ou effectuer une liaison pour cibler des propriétés qui acceptent des listes ou des collections. Si vous liez des collections, par exemple, vous liez un <xref:System.Windows.Controls.ListBox> qui s’étend en fonction du nombre d’éléments de données dans la collection, puis votre chemin de propriété doit référencer l’objet de collection, les éléments de collection individuels. Le moteur de liaison de données correspond à la collection utilisée comme source de données pour le type de la cible de liaison automatiquement, ce qui entraîne un comportement comme le remplissage d’un <xref:System.Windows.Controls.ListBox> avec un tableau d’éléments.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Propriété unique sur l’objet immédiat comme contexte de données

```xml
<Binding Path="propertyName" .../>
```

*propertyName* doit résoudre le nom d’une propriété qui est en cours <xref:System.Windows.FrameworkElement.DataContext%2A> pour un <xref:System.Windows.Data.Binding.Path%2A> l’utilisation. Si votre liaison met à jour la source, cette propriété doit être accessible en lecture/écriture et l’objet source doit être mutable.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Indexeur unique sur l’objet immédiat comme contexte de données

```xml
<Binding Path="[key]" .../>
```

`key` doit être l’index typé vers un dictionnaire ou une table de hachage, ou l’index entier d’un tableau. Par ailleurs, la valeur de la clé doit être un type pouvant être directement lié à la propriété sur laquelle il est appliqué. Par exemple, une table de hachage qui contient des clés et valeurs de chaîne peut servir de cette façon à lier au texte pour un <xref:System.Windows.Controls.TextBox>. Si la clé pointe vers une collection ou un sous-index, vous pouvez utiliser cette syntaxe pour effectuer une liaison à une propriété de collection cible. Sinon, vous devez référencer une propriété spécifique par le biais d’une syntaxe de type `<Binding Path="[key].propertyName" .../>`.

Vous pouvez spécifier le type de l’index si nécessaire. Pour plus d’informations sur cet aspect d’un chemin de propriété indexée, consultez <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Plusieurs propriétés (ciblage de propriété indirect)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName` doit correspondre au nom d’une propriété qui est en cours <xref:System.Windows.FrameworkElement.DataContext%2A>. Les propriétés de chemin `propertyName` et `propertyName2` peuvent être des propriétés qui existent dans une relation, où `propertyName2` est une propriété qui existe sur le type qui est la valeur de `propertyName`.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Propriété unique, jointe ou typée

```xml
<object property="(ownerType.propertyName)" .../>
```

Les parenthèses indiquent que cette propriété dans un <xref:System.Windows.PropertyPath> doit être construite à l’aide d’une qualification partielle. Elle peut utiliser un espace de noms XML pour rechercher le type avec un mappage approprié. Le `ownerType` recherche des types auxquels un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur peut accéder, via le <xref:System.Windows.Markup.XmlnsDefinitionAttribute> déclarations dans chaque assembly. Dans la plupart des applications, l’espace de noms XML par défaut est mappé à l’espace de noms [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. Un préfixe est donc généralement nécessaire uniquement pour les types personnalisés ou les types en dehors de cet espace de noms.  `propertyName` doit correspondre au nom d’une propriété existant sur le `ownerType`. Cette syntaxe est généralement utilisée pour l’un des cas suivants :

- Le chemin est spécifié dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui se trouve dans un style ou un modèle qui n’est pas un type de cible spécifié. Une utilisation qualifiée n’est généralement pas valide pour les autres cas, car dans les cas sans style ni modèle, la propriété existe sur une instance et non un type.

- La propriété est une propriété jointe.

- Vous effectuez une liaison à une propriété statique.

Pour une utilisation comme cible de la table de montage séquentiel, la propriété spécifiée en tant que `propertyName` doit être un <xref:System.Windows.DependencyProperty>.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Parcours de source (liaison avec des hiérarchies de collections)

```xml
<object Path="propertyName/propertyNameX" .../>
```

L’élément / de cette syntaxe est utilisé pour naviguer dans un objet de source de données hiérarchique. Plusieurs étapes dans la hiérarchie présentant des caractères / successifs sont prises en charge. Le parcours de source désigne la position du pointeur d’enregistrement actuel, qui est déterminée en synchronisant les données avec l’interface utilisateur de sa vue. Pour plus d’informations sur la liaison avec des objets de source de données hiérarchique et sur le concept de pointeur d’enregistrement actuel dans la liaison de données, consultez [Utiliser le modèle maître/détail avec des données hiérarchiques](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) ou [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).

> [!NOTE]
> En apparence, cette syntaxe ressemble à [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Un véritable [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] expression pour la liaison à un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source de données n’est pas utilisée comme un <xref:System.Windows.Data.Binding.Path%2A> valeur et doit plutôt être utilisée pour le mutuellement <xref:System.Windows.Data.Binding.XPath%2A> propriété.

### <a name="collection-views"></a>Vues de collection

Pour référencer une vue de collection nommée, faites précéder le nom de la vue de collection du caractère dièse (`#`).

### <a name="current-record-pointer"></a>Pointeur d’enregistrement actuel

Pour référencer le pointeur d’enregistrement actuel dans un scénario de vue de collection ou de liaison de données maître/détail, démarrez la chaîne de chemin par une barre oblique (`/`). Tous les chemins après la barre oblique sont parcourus à partir du pointeur d’enregistrement actuel.

### <a name="multiple-indexers"></a>Plusieurs indexeurs

```xaml
<object Path="[index1,index2...]" .../>
```

ou

```xaml
<object Path="propertyName[index,index2...]" .../>
```

Si un objet donné prend en charge plusieurs indexeurs, ces indexeurs peuvent être spécifiés dans l’ordre, comme une syntaxe de référencement de tableau. L’objet en question peut être le contexte actuel ou la valeur d’une propriété qui contient un objet avec plusieurs index.

Par défaut, les valeurs d’indexeur sont typées en utilisant les caractéristiques de l’objet sous-jacent. Vous pouvez spécifier le type de l’index si nécessaire. Pour plus d’informations sur le typage des indexeurs, consultez <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Mélange de syntaxes

Chacune des syntaxes ci-dessus peut être parsemée. Par exemple, ce qui suit est un exemple qui crée un chemin d’accès de propriété à la couleur à un particulier x, y d’un `ColorGrid` propriété qui contient un tableau de grille de pixels <xref:System.Windows.Media.SolidColorBrush> objets :

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Échappements pour les chaînes de chemin de propriété

Pour certains objets métiers, la chaîne de chemin de propriété peut nécessiter une séquence d’échappement pour effectuer correctement l’analyse. La nécessité d’une séquence d’échappement doit être rare, car la plupart de ces caractères ont des problèmes d’interactions de noms similaires dans les langages qui doivent normalement être utilisés pour définir l’objet métier.

- À l’intérieur des indexeurs ([ ]), le signe ^ échappe le caractère suivant.

- Vous devez échapper (à l’aide d’entités XML) certains caractères qui sont spécifiques de la définition de langage XML. Utilisez `&` pour échapper le caractère « & ». Utilisez `>` pour échapper la balise de fin « > ».

- Vous devez échapper (à l’aide de la barre oblique inverse `\`) les caractères spécifiques du comportement de l’analyseur XAML WPF pour le traitement d’une extension de balisage.

  - La barre oblique inverse (`\`) est le caractère d’échappement lui-même.

  - Le signe égal (`=`) sépare le nom et la valeur de la propriété.

  - La virgule (`,`) sépare les propriétés.

  - L’accolade fermante (`}`) marque la fin d’une extension de balisage.

> [!NOTE]
> Techniquement, ces échappements fonctionnent également pour un chemin de propriété de plan conceptuel, mais vous parcourez habituellement des modèles d’objet pour les objets WPF existants et l’échappement est inutile.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath pour les cibles d’animation

La propriété de cible d’une animation doit être une propriété de dépendance qui prend soit un <xref:System.Windows.Freezable> ou un type primitif. Toutefois, la propriété ciblée d’un type et la propriété animée éventuelle peuvent exister sur des objets différents. Pour les animations, un chemin de propriété permet de définir la connexion entre la propriété de l’objet cible de l’animation nommée et la propriété de l’animation cible prévue, en parcourant les relations objet-propriété dans les valeurs de propriété.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Considérations générales relatives à la relation objet-propriété des animations

Pour plus d’informations sur les concepts d’animation en général, consultez [Vue d’ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md) et [Vue d’ensemble des animations](../graphics-multimedia/animation-overview.md).

Le type de valeur ou la propriété animée doit être un <xref:System.Windows.Freezable> ou un type primitif. La propriété qui commence le chemin d’accès doit correspondre au nom d’une propriété de dépendance qui existe sur le texte spécifié <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.

Pour prendre en charge le clonage afin d’animer une <xref:System.Windows.Freezable> qui est déjà figé, l’objet spécifié par <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> doit être un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe dérivée.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Propriété unique sur l’objet cible

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName` doit être résolue en être le nom d’une propriété de dépendance qui existe sur le spécifié <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Ciblage de propriété indirect

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName` doit être une propriété qui est soit un <xref:System.Windows.Freezable> valeur ou un type primitif, qui existe sur le spécifié <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.

`propertyName2` doit être le nom d’une propriété de dépendance qui existe sur l’objet qui est la valeur de `propertyName`. En d’autres termes, `propertyName2` doit exister en tant que propriété de dépendance sur le type qui est la `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.

Le ciblage indirect d’animations est nécessaire en raison des styles et modèles appliqués. Pour cibler une animation, vous devez un <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> sur un objet cible et que le nom est établi par [x : Name](../../xaml-services/x-name-directive.md) ou <xref:System.Windows.FrameworkElement.Name%2A>. Bien que les éléments de modèle et de style peuvent également avoir des noms, ces noms sont uniquement valides au sein de la portée de nom du style et du modèle. (Si les styles et les modèles partagent des portées de nom avec un balisage d’application, les noms ne peuvent pas être uniques. Les styles et modèles sont littéralement partagés entre les instances et préservent les noms en double.) Par conséquent, si les propriétés individuelles d’un élément que vous voulez animer proviennent d’un style ou d’un modèle, vous devez commencer par une instance d’élément nommé qui ne vient pas d’un style ou d’un modèle, puis cibler l’arborescence de visuels du style ou du modèle pour accéder à la propriété que vous voulez animer.

Par exemple, le <xref:System.Windows.Controls.Panel.Background%2A> propriété d’un <xref:System.Windows.Controls.Panel> est complète <xref:System.Windows.Media.Brush> (en fait une <xref:System.Windows.Media.SolidColorBrush>) qui provient d’un modèle de thème. Pour animer un <xref:System.Windows.Media.Brush> complètement, il doit avoir un BrushAnimation (probablement un pour chaque <xref:System.Windows.Media.Brush> type) et il n’existe pas de type. Pour animer un Brush, vous devez plutôt animez les propriétés d’un particulier <xref:System.Windows.Media.Brush> type. Vous devez obtenir à partir de <xref:System.Windows.Media.SolidColorBrush> à son <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour appliquer un <xref:System.Windows.Media.Animation.ColorAnimation> il. Le chemin de propriété pour cet exemple est `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Propriétés jointes

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Les parenthèses indiquent que cette propriété dans un <xref:System.Windows.PropertyPath> doit être construite à l’aide d’une qualification partielle. Elle peut utiliser un espace de noms XML pour rechercher le type. Le `ownerType` recherche des types auxquels un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur peut accéder, via le <xref:System.Windows.Markup.XmlnsDefinitionAttribute> déclarations dans chaque assembly. Dans la plupart des applications, l’espace de noms XML par défaut est mappé à l’espace de noms [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. Un préfixe est donc généralement nécessaire uniquement pour les types personnalisés ou les types en dehors de cet espace de noms. `propertyName` doit correspondre au nom d’une propriété existant sur le `ownerType`. La propriété spécifiée en tant que `propertyName` doit être un <xref:System.Windows.DependencyProperty>. (Toutes les propriétés jointes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont implémentées sous forme de propriétés de dépendance, ce problème ne concerne donc que les propriétés jointes personnalisées.)

<a name="indexanim"></a>

### <a name="indexers"></a>Indexeurs

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

La plupart des propriétés de dépendance ou <xref:System.Windows.Freezable> types ne prennent pas en charge un indexeur. Par conséquent, la seule utilisation d’un indexeur dans un chemin d’animation est au niveau d’une position intermédiaire entre la propriété qui commence la chaîne sur la cible nommée et la propriété animée éventuelle. Dans la syntaxe fournie, il s’agit de `propertyName2`. Par exemple, utilisation d’un indexeur peut être nécessaire si la propriété intermédiaire est une collection comme <xref:System.Windows.Media.TransformGroup>, dans un chemin d’accès de propriété comme `RenderTransform.Children[1].Angle`.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath dans le code

Utilisation de code pour <xref:System.Windows.PropertyPath>, y compris comment construire un <xref:System.Windows.PropertyPath>, est documenté dans la rubrique de référence <xref:System.Windows.PropertyPath>.

En règle générale, <xref:System.Windows.PropertyPath> est conçu pour utiliser deux constructeurs différents, un pour les utilisations de liaison et les utilisations d’animation plus simples et un pour les utilisations des animations complexes. Utilisez le <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature d’une liaison, où l’objet est une chaîne. Utilisez le <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature pour les chemins d’animation en une seule étape, où l’objet est un <xref:System.Windows.DependencyProperty>. Utilisez le <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> signature pour les animations complexes. Ce dernier constructeur utilise une chaîne de jeton pour le premier paramètre et un tableau d’objets qui remplissent les positions de la chaîne de jeton pour définir une relation de chemin de propriété.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.PropertyPath>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Vue d'ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md)
