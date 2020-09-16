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
ms.openlocfilehash: ddaa35b18d1c632fc49b18dabf0d992dc1c78fcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549481"
---
# <a name="xname-directive"></a>x:Name, directive

Identifie de façon unique les éléments définis en XAML dans une portée de code XAML. Les portées de code XAML et leurs modèles d’unicité peuvent être appliqués aux objets instanciés, lorsque les infrastructures fournissent des API ou implémentent des comportements qui accèdent au graphique d’objet créé en XAML au moment de l’exécution.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`XAMLNameValue`|Chaîne conforme aux restrictions de la [grammaire XamlName](xamlname-grammar.md).|

## <a name="remarks"></a>Notes

Une fois que `x:Name` est appliqué au modèle de programmation de stockage d’une infrastructure, le nom est équivalent à la variable qui contient une référence d’objet ou une instance de retournée par un constructeur.

La valeur de l' `x:Name` utilisation d’une directive doit être unique dans une portée de code XAML. Par défaut lorsqu’elle est utilisée par l’API des services XAML .NET, la portée de code XAML principale est définie au niveau de l’élément racine XAML d’une production XAML unique et englobe les éléments contenus dans cette production XAML. Des portées de code XAML discrètes supplémentaires susceptibles de se produire dans une seule production XAML peuvent être définies par des infrastructures pour traiter des scénarios spécifiques. Par exemple, dans WPF, les nouvelles portées de code XAML sont définies et créées par n’importe quel modèle qui est également défini sur cette production XAML. Pour plus d’informations sur les portées de code XAML (écrites pour WPF, mais pertinentes pour de nombreux concepts de portée de code XAML), consultez portées de [code XAML WPF](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).

En général, `x:Name` ne doit pas être appliqué dans les situations qui utilisent également `x:Key` . Les implémentations XAML par des infrastructures existantes spécifiques ont introduit des concepts de substitution entre `x:Key` et `x:Name` , mais cela n’est pas une pratique recommandée. Les services XAML .NET ne prennent pas en charge les concepts de substitution de ce type lors de la gestion des informations de nom/clé, telles que <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .

Les règles d’autorisation de `x:Name` et de mise en application de l’unicité des noms sont potentiellement définies par des frameworks d’implémentation spécifiques. Toutefois, pour pouvoir être utilisé avec les services XAML .NET, les définitions d’infrastructure de l’unicité de la portée de code XAML doivent être cohérentes avec la définition des <xref:System.Windows.Markup.INameScope> informations dans cette documentation et doivent utiliser les mêmes règles relatives à l’emplacement d’application des informations. Par exemple, l' [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implémentation divise différents éléments de balisage en <xref:System.Windows.NameScope> plages distinctes, telles que les dictionnaires de ressources, l’arborescence logique créée par le code XAML au niveau de la page, les modèles et d’autres contenus différés, puis applique l’unicité des noms XAML dans chacune de ces portées de nom XAML.

Pour les types personnalisés qui utilisent les Writers d’objet XAML des services XAML .NET, une propriété qui mappe à `x:Name` sur un type peut être établie ou modifiée. Vous définissez ce comportement en référençant le nom de la propriété à mapper avec le <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> dans le code de définition de type.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> est un attribut de niveau type.

Les services XAML Using.NET, la logique de stockage pour la prise en charge de la portée de code XAML peut être définie de façon neutre au sein de l’infrastructure en implémentant l' <xref:System.Windows.Markup.INameScope> interface.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Dans la configuration de build standard d’une [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] application qui utilise XAML, des classes partielles et du code-behind, le spécifié `x:Name` devient le nom d’un champ créé dans le code sous-jacent lorsque [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] est traité par une tâche de génération de compilation du balisage, et ce champ contient une référence à l’objet. Par défaut, le champ créé est interne. Vous pouvez modifier l’accès aux champs en spécifiant l' [attribut x :FieldModifier](xfieldmodifier-directive.md). Dans WPF et Silverlight, la séquence est que la compilation du balisage définit et nomme le champ dans une classe partielle, mais la valeur est initialement vide. Ensuite, une méthode générée nommée `InitializeComponent` est appelée à partir du constructeur de classe. `InitializeComponent` se compose d' `FindName` appels à l’aide de chacune des `x:Name` valeurs qui existent dans la partie définie en XAML de la classe partielle en tant que chaînes d’entrée. Les valeurs de retour sont ensuite assignées à la référence de champ de nom similaire pour remplir les valeurs de champ avec les objets créés à partir de l’analyse XAML. L’exécution de vous permet de `InitializeComponent` référencer le graphique d’objet au moment de l’exécution à l’aide du `x:Name` nom de champ/directement, plutôt que d’appeler `FindName` explicitement chaque fois que vous avez besoin d’une référence à un objet défini en XAML.

Pour une application WPF qui utilise les cibles Microsoft Visual Basic et inclut des fichiers XAML avec l' `Page` action de génération, une propriété de référence distincte est créée pendant la compilation qui ajoute le `WithEvents` mot clé à tous les éléments qui ont un `x:Name` , pour prendre en charge la `Handles` syntaxe des délégués de gestionnaires d’événements. Cette propriété est toujours publique. Pour plus d’informations, consultez [Gestion des événements Visual Basic et WPF](/dotnet/desktop/wpf/advanced/visual-basic-and-wpf-event-handling).

`x:Name` est utilisé par le processeur XAML WPF pour inscrire un nom dans une portée de nom XAML au moment du chargement, même dans les cas où la page n’est pas compilée par balisage par des actions de génération (par exemple, le code XAML libre d’un dictionnaire de ressources). L’une des raisons de ce comportement est que le `x:Name` est potentiellement nécessaire pour la <xref:System.Windows.Data.Binding.ElementName%2A> liaison. Pour plus d’informations, consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.

Comme mentionné précédemment, `x:Name` (ou `Name` ) ne doit pas être appliqué dans les situations qui utilisent également `x:Key` . Le [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> a un comportement spécial qui se définit lui-même en tant que portée de code XAML, mais qui retourne des valeurs non implémentées ou null pour les <xref:System.Windows.Markup.INameScope> API pour appliquer ce comportement. Si l’analyseur XAML WPF rencontre `Name` ou `x:Name` dans un défini en XAML <xref:System.Windows.ResourceDictionary> , le nom n’est pas ajouté à une portée de nom XAML. Si vous tentez de trouver ce nom à partir d’une portée de nom XAML et que les `FindName` méthodes ne retournent pas de résultats valides.

### <a name="xname-and-name"></a>x :Name et Name

De nombreux scénarios d’application WPF peuvent éviter toute utilisation de l' `x:Name` attribut, car la `Name` propriété de dépendance telle qu’elle est spécifiée dans l’espace de noms XAML par défaut pour plusieurs classes de base importantes, telles que <xref:System.Windows.FrameworkElement> et <xref:System.Windows.FrameworkContentElement> satisfait le même objectif. Il existe toujours des scénarios XAML et WPF courants dans lesquels l’accès du code à un élément sans `Name` propriété au niveau de l’infrastructure est important. Par exemple, certaines classes d’animation et de prise en charge des storyboards ne prennent pas en charge une `Name` propriété, mais elles doivent souvent être référencées dans le code afin de contrôler l’animation. Vous devez spécifier `x:Name` comme attribut sur des chronologies et des transformations créées en XAML, si vous envisagez de les référencer à partir du code ultérieurement.

Si <xref:System.Windows.FrameworkElement.Name%2A> est disponible en tant que propriété sur la classe <xref:System.Windows.FrameworkElement.Name%2A> et `x:Name` peut être utilisé de manière interchangeable en tant qu’attributs, une exception d’analyse se produit si les deux sont spécifiés sur le même élément. Si le code XAML est compilé par balisage, l’exception se produit lors de la compilation du balisage. dans le cas contraire, il se produit lors du chargement.

<xref:System.Windows.FrameworkElement.Name%2A> peut être défini à l’aide de la syntaxe d’attribut XAML et dans le code à l’aide de <xref:System.Windows.DependencyObject.SetValue%2A> ; Notez toutefois que la définition <xref:System.Windows.FrameworkElement.Name%2A> de la propriété dans le code ne crée pas la référence de champ représentative dans la portée de code XAML dans la plupart des cas où le code XAML est déjà chargé. Au lieu d’essayer de définir <xref:System.Windows.FrameworkElement.Name%2A> dans le code, utilisez <xref:System.Windows.NameScope> des méthodes du code, par rapport à la portée de code appropriée.

<xref:System.Windows.FrameworkElement.Name%2A> peut également être défini à l’aide de la syntaxe d’élément de propriété avec du texte interne, mais cela n’est pas courant. En revanche, `x:Name` ne peut pas être défini dans la syntaxe d’élément de propriété XAML ou dans le code à l’aide de <xref:System.Windows.DependencyObject.SetValue%2A> ; il ne peut être défini qu’à l’aide de la syntaxe d’attribut sur les objets, car il s’agit d’une directive.

## <a name="silverlight-usage-notes"></a>Remarques sur l’utilisation de Silverlight

`x:Name` pour Silverlight est documenté séparément. Pour plus d’informations, consultez [espace de noms XAML (x :) Fonctionnalités de langage (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Arborescences dans WPF](/dotnet/desktop/wpf/advanced/trees-in-wpf)
