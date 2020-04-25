---
title: PropertyPath, syntaxe XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 817ce750cdad58e504eef5144cfb8a2813bca596
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141289"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath, syntaxe XAML

L' <xref:System.Windows.PropertyPath> objet prend en charge une syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Inline complexe pour définir différentes propriétés qui <xref:System.Windows.PropertyPath> prennent le type comme valeur. Cette rubrique documente <xref:System.Windows.PropertyPath> la syntaxe telle qu’elle est appliquée aux syntaxes de liaison et d’animation.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Cas d’utilisation de PropertyPath

<xref:System.Windows.PropertyPath>est un objet courant utilisé dans plusieurs [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionnalités. Malgré l’utilisation du <xref:System.Windows.PropertyPath> Common pour transmettre des informations de chemin d’accès à la propriété, les <xref:System.Windows.PropertyPath> utilisations de chaque domaine de fonctionnalité utilisées en tant que type varient. Par conséquent, il est plus pratique de documenter les syntaxes par fonctionnalité.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Utilise <xref:System.Windows.PropertyPath> principalement pour décrire les chemins d’accès de modèle objet pour parcourir les propriétés d’une source de données d’objet, et pour décrire le chemin d’accès cible pour les animations ciblées.

Certaines propriétés de style et de modèle <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> , telles que acceptent un nom de propriété qualifié qui ressemble <xref:System.Windows.PropertyPath>en apparence à un. Mais ce n’est pas vrai <xref:System.Windows.PropertyPath>. au lieu de cela, il s’agit d’un *propriétaire qualifié.* utilisation de format de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chaîne de propriété qui est activée par le <xref:System.Windows.DependencyProperty>processeur WPF en association avec le convertisseur de type pour.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath pour les objets dans la liaison de données

La liaison de données est une fonctionnalité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui permet d’effectuer une liaison à la valeur cible d’une propriété de dépendance. Toutefois, la source d’une liaison de données ne doit pas nécessairement être une propriété de dépendance, elle peut être n’importe quel type de propriété reconnu par le fournisseur de données applicable. Les chemins de propriété sont utilisés en <xref:System.Windows.Data.ObjectDataProvider>particulier pour le, qui est utilisé pour obtenir des sources de liaison à partir d’objets Common Language Runtime (CLR) et leurs propriétés.

Notez que la liaison de données à XML n' <xref:System.Windows.PropertyPath>utilise pas, car elle n' <xref:System.Windows.Data.Binding.Path%2A> utilise pas <xref:System.Windows.Data.Binding>dans le. Au lieu de cela <xref:System.Windows.Data.Binding.XPath%2A> , vous utilisez et spécifiez une syntaxe XPath valide dans le document Object Model XML (DOM) des données. <xref:System.Windows.Data.Binding.XPath%2A>est également spécifié sous forme de chaîne, mais n’est pas documenté ici ; consultez [lier à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Un élément essentiel qui permet de comprendre les chemins de propriété dans la liaison de données est que vous pouvez cibler la liaison à une valeur de propriété individuelle, ou effectuer une liaison pour cibler des propriétés qui acceptent des listes ou des collections. Si vous liez des collections, par exemple une <xref:System.Windows.Controls.ListBox> liaison qui se développe en fonction du nombre d’éléments de données présents dans la collection, votre chemin de propriété doit référencer l’objet de collection, et non des éléments de collection individuels. Le moteur de liaison de données met automatiquement en correspondance la collection utilisée comme source de données avec le type de la cible de liaison, ce qui entraîne <xref:System.Windows.Controls.ListBox> un comportement tel que le remplissage d’un avec un tableau d’éléments.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Propriété unique sur l’objet immédiat comme contexte de données

```xml
<Binding Path="propertyName" ... />
```

*PropertyName* doit correspondre au nom d’une propriété qui se trouve dans le actuel <xref:System.Windows.FrameworkElement.DataContext%2A> pour une <xref:System.Windows.Data.Binding.Path%2A> utilisation. Si votre liaison met à jour la source, cette propriété doit être accessible en lecture/écriture et l’objet source doit être mutable.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Indexeur unique sur l’objet immédiat comme contexte de données

```xml
<Binding Path="[key]" ... />
```

`key` doit être l’index typé vers un dictionnaire ou une table de hachage, ou l’index entier d’un tableau. Par ailleurs, la valeur de la clé doit être un type pouvant être directement lié à la propriété sur laquelle il est appliqué. Par exemple, une table de hachage qui contient des clés de chaîne et des valeurs de chaîne peut être utilisée de cette façon <xref:System.Windows.Controls.TextBox>pour effectuer une liaison à du texte pour un. Si la clé pointe vers une collection ou un sous-index, vous pouvez utiliser cette syntaxe pour effectuer une liaison à une propriété de collection cible. Sinon, vous devez référencer une propriété spécifique par le biais d’une syntaxe de type `<Binding Path="[key].propertyName" .../>`.

Vous pouvez spécifier le type de l’index si nécessaire. Pour plus d’informations sur cet aspect d’un chemin d’accès à <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>une propriété indexée, consultez.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Plusieurs propriétés (ciblage de propriété indirect)

```xml
<Binding Path="propertyName.propertyName2" ... />
```

`propertyName`doit correspondre au nom d’une propriété qui est le actuel <xref:System.Windows.FrameworkElement.DataContext%2A>. Les propriétés de chemin `propertyName` et `propertyName2` peuvent être des propriétés qui existent dans une relation, où `propertyName2` est une propriété qui existe sur le type qui est la valeur de `propertyName`.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Propriété unique, jointe ou typée

```xml
<object property="(ownerType.propertyName)" ... />
```

Les parenthèses indiquent que cette propriété dans un <xref:System.Windows.PropertyPath> doit être construite à l’aide d’une qualification partielle. Elle peut utiliser un espace de noms XML pour rechercher le type avec un mappage approprié. Recherche `ownerType` les types auxquels un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur a accès, via les <xref:System.Windows.Markup.XmlnsDefinitionAttribute> déclarations de chaque assembly. Dans la plupart des applications, l’espace de noms XML par défaut est mappé à l’espace de noms `http://schemas.microsoft.com/winfx/2006/xaml/presentation`. Un préfixe est donc généralement nécessaire uniquement pour les types personnalisés ou les types en dehors de cet espace de noms.  `propertyName` doit correspondre au nom d’une propriété existant sur le `ownerType`. Cette syntaxe est généralement utilisée pour l’un des cas suivants :

- Le chemin est spécifié dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui se trouve dans un style ou un modèle qui n’est pas un type de cible spécifié. Une utilisation qualifiée n’est généralement pas valide pour les autres cas, car dans les cas sans style ni modèle, la propriété existe sur une instance et non un type.

- La propriété est une propriété jointe.

- Vous effectuez une liaison à une propriété statique.

Pour une utilisation en tant que cible de Storyboard, `propertyName` la propriété spécifiée <xref:System.Windows.DependencyProperty>comme doit être un.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Parcours de source (liaison avec des hiérarchies de collections)

```xml
<object Path="propertyName/propertyNameX" ... />
```

L’élément / de cette syntaxe est utilisé pour naviguer dans un objet de source de données hiérarchique. Plusieurs étapes dans la hiérarchie présentant des caractères / successifs sont prises en charge. Le parcours de source désigne la position du pointeur d’enregistrement actuel, qui est déterminée en synchronisant les données avec l’interface utilisateur de sa vue. Pour plus d’informations sur la liaison avec des objets de source de données hiérarchique et sur le concept de pointeur d’enregistrement actuel dans la liaison de données, consultez [Utiliser le modèle maître/détail avec des données hiérarchiques](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) ou [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).

> [!NOTE]
> En apparence, cette syntaxe ressemble à XPath. Une expression XPath vraie pour la liaison à une source de données XML n’est pas <xref:System.Windows.Data.Binding.Path%2A> utilisée comme valeur et doit plutôt être utilisée pour la <xref:System.Windows.Data.Binding.XPath%2A> propriété s’excluant mutuellement.

### <a name="collection-views"></a>Vues de collection

Pour référencer une vue de collection nommée, faites précéder le nom de la vue de collection du caractère dièse (`#`).

### <a name="current-record-pointer"></a>Pointeur d’enregistrement actuel

Pour référencer le pointeur d’enregistrement actuel dans un scénario de vue de collection ou de liaison de données maître/détail, démarrez la chaîne de chemin par une barre oblique (`/`). Tous les chemins après la barre oblique sont parcourus à partir du pointeur d’enregistrement actuel.

### <a name="multiple-indexers"></a>Plusieurs indexeurs

```xaml
<object Path="[index1,index2...]" ... />
```

ou

```xaml
<object Path="propertyName[index,index2...]" ... />
```

Si un objet donné prend en charge plusieurs indexeurs, ces indexeurs peuvent être spécifiés dans l’ordre, comme une syntaxe de référencement de tableau. L’objet en question peut être le contexte actuel ou la valeur d’une propriété qui contient un objet avec plusieurs index.

Par défaut, les valeurs d’indexeur sont typées en utilisant les caractéristiques de l’objet sous-jacent. Vous pouvez spécifier le type de l’index si nécessaire. Pour plus d’informations sur la saisie des indexeurs, consultez <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Mélange de syntaxes

Chacune des syntaxes ci-dessus peut être parsemée. Par exemple, voici un exemple qui crée un chemin de propriété vers la couleur à un x, y particulier d’une `ColorGrid` propriété qui contient un tableau de grille de pixels <xref:System.Windows.Media.SolidColorBrush> d’objets :

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" ... />
```

### <a name="escapes-for-property-path-strings"></a>Échappements pour les chaînes de chemin de propriété

Pour certains objets métiers, la chaîne de chemin de propriété peut nécessiter une séquence d’échappement pour effectuer correctement l’analyse. La nécessité d’une séquence d’échappement doit être rare, car la plupart de ces caractères ont des problèmes d’interactions de noms similaires dans les langages qui doivent normalement être utilisés pour définir l’objet métier.

- À l’intérieur des indexeurs ([]), l’accent circonflexe (^) échappe le caractère suivant.

- Vous devez échapper (à l’aide d’entités XML) certains caractères qui sont spécifiques de la définition de langage XML. Utilisez `&` pour échapper le caractère « & ». Utilisez `>` pour échapper la balise de fin « > ».

- Vous devez échapper (à l’aide de la barre oblique inverse `\`) les caractères spécifiques du comportement de l’analyseur XAML WPF pour le traitement d’une extension de balisage.

  - La barre oblique inverse (`\`) est le caractère d’échappement lui-même.

  - Le signe égal (`=`) sépare le nom et la valeur de la propriété.

  - La virgule (`,`) sépare les propriétés.

  - L’accolade fermante (`}`) marque la fin d’une extension de balisage.

> [!NOTE]
> Techniquement, ces échappements fonctionnent également pour un chemin de propriété de plan conceptuel, mais vous parcourez habituellement des modèles d’objet pour les objets WPF existants et l’échappement est inutile.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath pour les cibles d’animation

La propriété cible d’une animation doit être une propriété de dépendance qui accepte un <xref:System.Windows.Freezable> ou un type primitif. Toutefois, la propriété ciblée d’un type et la propriété animée éventuelle peuvent exister sur des objets différents. Pour les animations, un chemin de propriété permet de définir la connexion entre la propriété de l’objet cible de l’animation nommée et la propriété de l’animation cible prévue, en parcourant les relations objet-propriété dans les valeurs de propriété.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Considérations générales relatives à la relation objet-propriété des animations

Pour plus d’informations sur les concepts d’animation en général, consultez [Vue d’ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md) et [Vue d’ensemble des animations](../graphics-multimedia/animation-overview.md).

Le type de valeur ou la propriété animée doit être un <xref:System.Windows.Freezable> type ou une primitive. La propriété qui démarre le chemin doit correspondre au nom d’une propriété de dépendance qui existe sur le type spécifié <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> .

Pour prendre en charge le clonage afin <xref:System.Windows.Freezable> d’animer un qui est déjà gelé, l’objet <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> spécifié par doit <xref:System.Windows.FrameworkElement> être <xref:System.Windows.FrameworkContentElement> une classe ou dérivée.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Propriété unique sur l’objet cible

```xml
<animation Storyboard.TargetProperty="propertyName" ... />
```

`propertyName`doit correspondre au nom d’une propriété de dépendance qui existe sur le type spécifié <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> .

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Ciblage de propriété indirect

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" ... />
```

`propertyName`doit être une propriété qui est soit un <xref:System.Windows.Freezable> type valeur, soit une primitive, qui existe sur le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type spécifié.

`propertyName2` doit être le nom d’une propriété de dépendance qui existe sur l’objet qui est la valeur de `propertyName`. En d’autres termes `propertyName2` , doit exister en tant que propriété de dépendance sur le type `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>qui est le.

Le ciblage indirect d’animations est nécessaire en raison des styles et modèles appliqués. Pour cibler une animation, vous avez besoin d’un <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> sur un objet cible et ce nom est établi par [x :Name](../../../desktop-wpf/xaml-services/xname-directive.md) ou <xref:System.Windows.FrameworkElement.Name%2A>. Bien que les éléments de modèle et de style peuvent également avoir des noms, ces noms sont uniquement valides au sein de la portée de nom du style et du modèle. (Si les styles et les modèles partagent des portées de nom avec un balisage d’application, les noms ne peuvent pas être uniques. Les styles et les modèles sont littéralement partagés entre les instances et perpétuer des noms dupliqués.) Ainsi, si les propriétés individuelles d’un élément que vous souhaitez animer proviennent d’un style ou d’un modèle, vous devez commencer par une instance d’élément nommé qui ne provient pas d’un modèle de style, puis cibler dans l’arborescence d’éléments visuels du style ou du modèle pour arriver à la propriété que vous souhaitez animer.

Par exemple, la <xref:System.Windows.Controls.Panel.Background%2A> propriété d’un <xref:System.Windows.Controls.Panel> est une complète <xref:System.Windows.Media.Brush> (en fait <xref:System.Windows.Media.SolidColorBrush>) qui provient d’un modèle de thème. Pour animer <xref:System.Windows.Media.Brush> complètement un, il doit exister un BrushAnimation (probablement un pour chaque <xref:System.Windows.Media.Brush> type) et il n’y a pas de type de ce type. Pour animer un pinceau, vous animez à la place <xref:System.Windows.Media.Brush> les propriétés d’un type particulier. Vous devez passer de <xref:System.Windows.Media.SolidColorBrush> à son <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour y appliquer un <xref:System.Windows.Media.Animation.ColorAnimation> . Le chemin de propriété pour cet exemple est `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Propriétés jointes

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" ... />
```

Les parenthèses indiquent que cette propriété dans un <xref:System.Windows.PropertyPath> doit être construite à l’aide d’une qualification partielle. Elle peut utiliser un espace de noms XML pour rechercher le type. Recherche `ownerType` les types auxquels un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur a accès, via les <xref:System.Windows.Markup.XmlnsDefinitionAttribute> déclarations de chaque assembly. Dans la plupart des applications, l’espace de noms XML par défaut est mappé à l’espace de noms `http://schemas.microsoft.com/winfx/2006/xaml/presentation`. Un préfixe est donc généralement nécessaire uniquement pour les types personnalisés ou les types en dehors de cet espace de noms. `propertyName` doit correspondre au nom d’une propriété existant sur le `ownerType`. La propriété spécifiée comme `propertyName` doit être <xref:System.Windows.DependencyProperty>. (Toutes les propriétés jointes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont implémentées sous forme de propriétés de dépendance, ce problème ne concerne donc que les propriétés jointes personnalisées.)

<a name="indexanim"></a>

### <a name="indexers"></a>Indexeurs

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" ... />
```

La plupart des propriétés <xref:System.Windows.Freezable> ou types de dépendance ne prennent pas en charge un indexeur. Par conséquent, la seule utilisation d’un indexeur dans un chemin d’animation est au niveau d’une position intermédiaire entre la propriété qui commence la chaîne sur la cible nommée et la propriété animée éventuelle. Dans la syntaxe fournie, il s’agit de `propertyName2`. Par exemple, l’utilisation d’un indexeur peut être nécessaire si la propriété intermédiaire est une collection <xref:System.Windows.Media.TransformGroup>telle que, dans un chemin de `RenderTransform.Children[1].Angle`propriété tel que.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath dans le code

L’utilisation du <xref:System.Windows.PropertyPath>code pour, y compris la <xref:System.Windows.PropertyPath>construction d’un, est documentée dans <xref:System.Windows.PropertyPath>la rubrique de référence pour.

En général, <xref:System.Windows.PropertyPath> est conçu pour utiliser deux constructeurs différents, l’un pour les utilisations de liaison et les utilisations d’animation les plus simples, et l’autre pour les utilisations d’animation complexes. Utilisez la <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature pour lier les utilisations, où l’objet est une chaîne. Utilisez la <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature pour les chemins d’animation à une étape, où l’objet <xref:System.Windows.DependencyProperty>est un. Utilisez la <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> signature pour les animations complexes. Ce dernier constructeur utilise une chaîne de jeton pour le premier paramètre et un tableau d’objets qui remplissent les positions de la chaîne de jeton pour définir une relation de chemin de propriété.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.PropertyPath>
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d'ensemble des storyboards](../graphics-multimedia/storyboards-overview.md)
