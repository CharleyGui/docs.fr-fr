---
title: x:Name, directive
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071450"
---
# <a name="xname-directive"></a>x:Name, directive

Identifie uniquement les éléments définis par XAML dans un namescope XAML. Les namescopes XAML et leurs modèles d’unicité peuvent être appliqués aux objets instantanés, lorsque les cadres fournissent des API ou implémentent des comportements qui accèdent au graphique d’objets créé par XAML au moment de l’exécution.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`XAMLNameValue`|Une chaîne conforme aux restrictions de la [grammaire XamlName](xamlname-grammar.md).|

## <a name="remarks"></a>Notes

Une `x:Name` fois appliqué au modèle de programmation d’accompagnement d’un cadre, le nom est équivalent à la variable qui contient une référence d’objet ou une instance telle qu’elle est retournée par un constructeur.

La valeur `x:Name` d’une utilisation directive doit être unique dans un namescope XAML. Par défaut lorsqu’il est utilisé par .NET XAML Services API, le nomscope XAML primaire est défini à l’élément racine XAML d’une seule production XAML, et englobe les éléments qui sont contenus dans cette production XAML. D’autres namescopes XAML discrets qui pourraient se produire dans une seule production XAML peuvent être définis par des cadres pour aborder des scénarios spécifiques. Par exemple, dans WPF, de nouveaux namescopes XAML sont définis et créés par n’importe quel modèle qui est également défini sur cette production XAML. Pour plus d’informations sur les namescopes XAML (écrits pour WPF mais pertinents pour de nombreux concepts de namescope XAML), voir [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

En général, `x:Name` ne doit pas être `x:Key`appliqué dans les situations qui utilisent également . Les implémentations XAML par des `x:Key` `x:Name`cadres existants spécifiques ont introduit des concepts de substitution entre et , mais ce n’est pas une pratique recommandée. .NET XAML Services ne prend pas en charge de <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>tels concepts de substitution lors du traitement des informations de nom/clés telles que ou .

Les règles relatives `x:Name` à l’application de la permis ainsi que l’application de l’unicité des noms sont potentiellement définies par des cadres de mise en œuvre spécifiques. Toutefois, pour être utilisables avec .NET XAML Services, les définitions-cadres de <xref:System.Windows.Markup.INameScope> l’unicité XAML namescope devraient être compatibles avec la définition de l’information dans cette documentation, et devraient utiliser les mêmes règles concernant l’endroit où l’information est appliquée. Par exemple, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] l’implémentation divise <xref:System.Windows.NameScope> divers éléments de balisage en plages distinctes, telles que les dictionnaires de ressources, l’arbre logique créé par la page XAML, les modèles et autres contenus différés, puis applique l’unicité du nom XAML dans chacun de ces namescopes XAML.

Pour les types personnalisés qui utilisent .NET XAML Services `x:Name` XAML auteurs d’objets, une propriété que les cartes à un type peut être établi ou modifié. Vous définissez ce comportement en faisant référence au <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> nom de la propriété pour cartographier le code de définition du type.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>est un attribut de type.

Using.NET XAML Services, la logique de support pour le support de namescope XAML <xref:System.Windows.Markup.INameScope> peut être définie d’une manière neutre en implémentant l’interface.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

En vertu de la [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] configuration de construction standard pour une application qui `x:Name` utilise XAML, classes partielles, et [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] de code-derrière, le spécifié devient le nom d’un champ qui est créé dans le code sous-jacent quand est traité par une tâche de compilation de balisage, et ce champ détient une référence à l’objet. Par défaut, le champ créé est interne. Vous pouvez modifier l’accès au champ en spécifiant [l’attribut x:FieldModifier](xfieldmodifier-directive.md). Dans WPF et Silverlight, la séquence est que la compilation de balisage définit et nomme le champ dans une classe partielle, mais la valeur est initialement vide. Ensuite, une méthode `InitializeComponent` générée nommée est appelée de l’intérieur du constructeur de classe. `InitializeComponent`se `FindName` compose d’appels `x:Name` utilisant chacune des valeurs qui existent dans la partie XAML définie de la classe partielle comme des chaînes d’entrée. Les valeurs de retour sont ensuite attribuées à la référence de champ nommée comme pour remplir les valeurs de champ avec des objets qui ont été créés à partir de l’analyse XAML. L’exécution `InitializeComponent` de permettre de référencer le `x:Name` graphique d’objet de temps `FindName` d’exécution en utilisant le nom / champ directement, plutôt que d’avoir à appeler explicitement chaque fois que vous avez besoin d’une référence à un objet XAML défini.

Pour une application WPF qui utilise les cibles Microsoft `Page` Visual Basic et comprend des fichiers XAML avec action de construction, une propriété de référence distincte est créée au cours de la compilation qui ajoute le `WithEvents` mot clé à tous les éléments qui ont une `x:Name`syntaxe , pour prendre en charge `Handles` la syntaxe pour les délégués gestionnaire d’événements. Cette propriété est toujours publique. Pour plus d’informations, consultez [Gestion des événements Visual Basic et WPF](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).

`x:Name`est utilisé par le processeur WPF XAML pour enregistrer un nom dans un namescope XAML au moment de la charge, même pour les cas où la page n’est pas compilée par des actions de construction (par exemple, en vrac XAML d’un dictionnaire de ressources). Une des raisons de `x:Name` ce comportement <xref:System.Windows.Data.Binding.ElementName%2A> est parce que le est potentiellement nécessaire pour la liaison. Pour plus de détails, voir [Aperçu de liaison de données](../data/data-binding-overview.md).

Comme mentionné `x:Name` précédemment, `Name`(ou ) ne doit `x:Key`pas être appliqué dans les situations qui utilisent également . Le [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> a un comportement particulier de se définir comme un namescope <xref:System.Windows.Markup.INameScope> XAML, mais le retour non mis en œuvre ou des valeurs nulles pour les API comme un moyen d’appliquer ce comportement. Si le parser WPF `Name` XAML rencontre ou `x:Name` <xref:System.Windows.ResourceDictionary>dans un XAML défini, le nom n’est pas ajouté à un namescope XAML. Tenter de trouver ce nom à partir `FindName` d’un namescope XAML et les méthodes ne retournera pas les résultats valides.

### <a name="xname-and-name"></a>x:Nom et nom

De nombreux scénarios d’application WPF `x:Name` peuvent éviter `Name` toute utilisation de l’attribut, parce que la propriété de <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> dépendance comme spécifié dans l’espace de nom XAML par défaut pour plusieurs des classes de base importantes telles que et satisfait ce même but. Il existe encore des scénarios communs de XAML et de `Name` WPF où l’accès au code à un élément sans propriété au niveau du cadre est important. Par exemple, certaines classes de support d’animation et de storyboard ne prennent pas en charge une `Name` propriété, mais elles doivent souvent être référencées en code afin de contrôler l’animation. Vous devez `x:Name` spécifier comme attribut sur les délais et les transformations qui sont créés dans XAML, si vous avez l’intention de les référer à partir de code plus tard.

Si <xref:System.Windows.FrameworkElement.Name%2A> elle est disponible comme <xref:System.Windows.FrameworkElement.Name%2A> une `x:Name` propriété sur la classe, et peut être utilisé de façon interchangeable comme attributs, mais une exception d’analyse se traduira si les deux sont spécifiés sur le même élément. Si le XAML est compilé, l’exception se produira sur la compilation de balisage, sinon elle se produit sur la charge.

<xref:System.Windows.FrameworkElement.Name%2A>peut être réglé à l’aide de la <xref:System.Windows.DependencyObject.SetValue%2A>syntaxe d’attribut XAML, et dans le code à l’aide de ; notez toutefois <xref:System.Windows.FrameworkElement.Name%2A> que la définition de la propriété dans le code ne crée pas la référence de champ représentative dans le namescope XAML dans la plupart des circonstances où le XAML est déjà chargé. Au lieu d’essayer de définir <xref:System.Windows.FrameworkElement.Name%2A> dans le code, utilisez <xref:System.Windows.NameScope> des méthodes à partir du code, contre le namescope approprié.

<xref:System.Windows.FrameworkElement.Name%2A>peut également être réglé en utilisant la syntaxe d’élément de propriété avec le texte intérieur, mais c’est rare. En revanche, `x:Name` ne peut pas être mis en syntaxe élément de propriété XAML, ou dans le code en utilisant <xref:System.Windows.DependencyObject.SetValue%2A>; il ne peut être réglé qu’à l’aide de la syntaxe d’attribut sur les objets parce qu’il s’agit d’une directive.

## <a name="silverlight-usage-notes"></a>Notes d’utilisation Silverlight

`x:Name`pour Silverlight est documenté séparément. Pour plus d’informations, voir [XAML Namespace (x:) Caractéristiques linguistiques (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Arborescences dans WPF](../../framework/wpf/advanced/trees-in-wpf.md)
