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
ms.openlocfilehash: d17d977384962980839fbe2b2c0a4708412d403d
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837218"
---
# <a name="xname-directive"></a>x:Name, directive
Identifie de façon unique les éléments définis en XAML dans une portée de code XAML. Les portées de code XAML et leurs modèles d’unicité peuvent être appliqués aux objets instanciés, lorsque les infrastructures fournissent des API ou implémentent des comportements qui accèdent au graphique d’objet créé en XAML au moment de l’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Chaîne conforme aux restrictions de la [grammaire XamlName](xamlname-grammar.md).|  
  
## <a name="remarks"></a>Notes  
 Une fois que `x:Name` est appliqué au modèle de programmation de stockage d’une infrastructure, le nom est équivalent à la variable qui contient une référence d’objet ou une instance de retournée par un constructeur.  
  
 La valeur de l’utilisation d’une directive `x:Name` doit être unique dans une portée de code XAML. Par défaut lorsqu’il est utilisé par .NET Framework API des services XAML, la portée de code XAML principale est définie au niveau de l’élément racine XAML d’une production XAML unique et englobe les éléments contenus dans cette production XAML. Des portées de code XAML discrètes supplémentaires susceptibles de se produire dans une seule production XAML peuvent être définies par des infrastructures pour traiter des scénarios spécifiques. Par exemple, dans WPF, les nouvelles portées de code XAML sont définies et créées par n’importe quel modèle qui est également défini sur cette production XAML. Pour plus d’informations sur les portées de code XAML (écrites pour WPF, mais pertinentes pour de nombreux concepts de portée de code XAML), consultez portées de [code XAML WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 En général, `x:Name` ne doit pas être appliqué dans les situations qui utilisent également `x:Key`. Les implémentations XAML par des infrastructures existantes spécifiques ont introduit des concepts de substitution entre `x:Key` et `x:Name`, mais cela n’est pas une pratique recommandée. Les services XAML .NET Framework ne prennent pas en charge les concepts de substitution de ce type lors de la gestion des informations de nom/clé, telles que <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Les règles d’autorisation des `x:Name`, ainsi que la mise en application de l’unicité des noms, sont potentiellement définies par des frameworks d’implémentation spécifiques. Toutefois, pour pouvoir être utilisé avec .NET Framework les services XAML, les définitions d’infrastructure de l’unicité de la portée de code XAML doivent être cohérentes avec la définition des informations d' <xref:System.Windows.Markup.INameScope> dans cette documentation et doivent utiliser les mêmes règles relatives à l’emplacement d’application des informations. Par exemple, l’implémentation de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] divise différents éléments de balisage en plages <xref:System.Windows.NameScope> distinctes, telles que les dictionnaires de ressources, l’arborescence logique créée par le code XAML au niveau de la page, les modèles et d’autres contenus différés, puis applique l’unicité des noms XAML dans chacune de ces portées de nom XAML.  
  
 Pour les types personnalisés qui utilisent .NET Framework Writers d’objet XAML des services XAML, une propriété qui mappe à `x:Name` sur un type peut être établie ou modifiée. Vous définissez ce comportement en référençant le nom de la propriété à mapper avec les <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> dans le code de définition de type.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> est un attribut de niveau type.  
  
 Services XAML Using.NET Framework, la logique de stockage pour la prise en charge de la portée de code XAML peut être définie de façon indépendante du point de vue en implémentant l’interface <xref:System.Windows.Markup.INameScope>.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Dans le cadre de la configuration de build standard pour une application [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui utilise XAML, des classes partielles et du code-behind, la `x:Name` spécifiée devient le nom d’un champ créé dans le code sous-jacent lorsque [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] est traité par une tâche de génération de compilation du balisage, et ce champ contient une référence à l’objet. Par défaut, le champ créé est interne. Vous pouvez modifier l’accès aux champs en spécifiant l' [attribut x :FieldModifier](x-fieldmodifier-directive.md). Dans WPF et Silverlight, la séquence est que la compilation du balisage définit et nomme le champ dans une classe partielle, mais la valeur est initialement vide. Ensuite, une méthode générée nommée `InitializeComponent` est appelée à partir du constructeur de classe. `InitializeComponent` se compose d' `FindName` appels à l’aide de chacune des valeurs de `x:Name` qui existent dans la partie définie en XAML de la classe partielle en tant que chaînes d’entrée. Les valeurs de retour sont ensuite assignées à la référence de champ de nom similaire pour remplir les valeurs de champ avec les objets créés à partir de l’analyse XAML. L’exécution de `InitializeComponent` permet de référencer le graphique d’objet au moment de l’exécution en utilisant directement le nom de `x:Name`/champ, plutôt que d’appeler `FindName` explicitement chaque fois que vous avez besoin d’une référence à un objet défini en XAML.  
  
 Pour une application WPF qui utilise les cibles Microsoft Visual Basic et inclut des fichiers XAML avec `Page` action de génération, une propriété de référence distincte est créée pendant la compilation qui ajoute le mot clé `WithEvents` à tous les éléments qui ont un `x:Name`, pour prendre en charge `Handles` syntaxe pour les délégués de gestionnaires d’événements. Cette propriété est toujours publique. Pour plus d’informations, consultez [Gestion des événements Visual Basic et WPF](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` est utilisé par le processeur XAML WPF pour inscrire un nom dans une portée de nom XAML au moment du chargement, même dans les cas où la page n’est pas compilée par balisage par des actions de génération (par exemple, le code XAML libre d’un dictionnaire de ressources). Ce comportement peut être dû au fait que le `x:Name` est potentiellement nécessaire pour la liaison <xref:System.Windows.Data.Binding.ElementName%2A>. Pour plus d’informations, consultez [vue d’ensemble](../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.  
  
 Comme mentionné précédemment, `x:Name` (ou `Name`) ne doit pas être appliqué dans les situations qui utilisent également `x:Key`. Le <xref:System.Windows.ResourceDictionary> [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] a un comportement spécial qui se définit lui-même en tant que portée de code XAML, mais qui retourne des valeurs non implémentées ou null pour les API <xref:System.Windows.Markup.INameScope> comme un moyen d’appliquer ce comportement. Si l’analyseur XAML WPF rencontre `Name` ou `x:Name` dans un <xref:System.Windows.ResourceDictionary>défini en XAML, le nom n’est pas ajouté à une portée de nom XAML. Toute tentative de recherche de ce nom à partir d’une portée de nom XAML et des méthodes `FindName` ne retourne pas de résultats valides.  
  
### <a name="xname-and-name"></a>x :Name et Name  
 De nombreux scénarios d’application WPF peuvent éviter toute utilisation de l’attribut `x:Name`, car l' `Name` propriété de dépendance telle qu’elle est spécifiée dans l’espace de noms XAML par défaut pour plusieurs classes de base importantes, telles que <xref:System.Windows.FrameworkElement> et <xref:System.Windows.FrameworkContentElement> remplit ce même objectif. Il existe toujours des scénarios XAML et WPF courants dans lesquels le code qui accède à un élément sans `Name` propriété au niveau de l’infrastructure est important. Par exemple, certaines classes d’animation et de prise en charge des storyboards ne prennent pas en charge une propriété `Name`, mais elles doivent souvent être référencées dans le code afin de contrôler l’animation. Vous devez spécifier `x:Name` en tant qu’attribut sur les chronologies et les transformations créées en XAML, si vous envisagez de les référencer à partir du code ultérieurement.  
  
 Si <xref:System.Windows.FrameworkElement.Name%2A> est disponible en tant que propriété sur la classe, <xref:System.Windows.FrameworkElement.Name%2A> et `x:Name` peuvent être utilisés de manière interchangeable en tant qu’attributs, mais une exception d’analyse se produit si les deux sont spécifiés sur le même élément. Si le code XAML est compilé par balisage, l’exception se produit lors de la compilation du balisage. dans le cas contraire, il se produit lors du chargement.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> peut être défini à l’aide de la syntaxe d’attribut XAML et dans le code à l’aide de <xref:System.Windows.DependencyObject.SetValue%2A>; Notez cependant que la définition de la propriété <xref:System.Windows.FrameworkElement.Name%2A> dans le code ne crée pas la référence de champ représentative dans la portée de code XAML dans la plupart des cas où le code XAML est déjà chargé. Au lieu de tenter de définir <xref:System.Windows.FrameworkElement.Name%2A> dans le code, utilisez <xref:System.Windows.NameScope> méthodes à partir du code, par rapport à la portée de code appropriée.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> peut également être défini à l’aide de la syntaxe d’élément de propriété avec du texte interne, mais cela n’est pas courant. En revanche, `x:Name` ne peut pas être défini dans la syntaxe d’élément de propriété XAML ou dans le code à l’aide de <xref:System.Windows.DependencyObject.SetValue%2A>; elle ne peut être définie qu’à l’aide de la syntaxe d’attribut sur les objets, car il s’agit d’une directive.  
  
## <a name="silverlight-usage-notes"></a>Notes d'utilisation de Silverlight  
 `x:Name` pour Silverlight est documenté séparément. Pour plus d’informations, consultez [espace de noms XAML (x :) Fonctionnalités de langage (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Arborescences dans WPF](../wpf/advanced/trees-in-wpf.md)
