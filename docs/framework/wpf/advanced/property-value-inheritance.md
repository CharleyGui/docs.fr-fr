---
title: Héritage de la valeur de propriété
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: eb757d039437d9954a2b648c5f758dffa3fee3d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958362"
---
# <a name="property-value-inheritance"></a>Héritage de la valeur de propriété
L’héritage de la valeur de propriété est une fonctionnalité du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. L’héritage de la valeur de propriété permet aux éléments enfants d’une arborescence d’éléments d’obtenir la valeur d’une propriété particulière des éléments parents, en héritant cette valeur telle qu’elle a été définie dans l’élément parent le plus proche. L’élément parent peut également avoir obtenu sa valeur par héritage de la valeur de propriété, le système peut donc remonter jusqu’à la racine de la page. L’héritage de la valeur de propriété n’est pas le comportement du système de propriétés par défaut. Une propriété doit être établie avec un paramètre de métadonnées particulier pour pouvoir lancer l’héritage de la valeur de propriété sur les éléments enfants.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>L’héritage de la valeur de propriété est un héritage de relation contenant-contenu  
 Le terme « Héritage » ne désigne pas tout à fait le même concept que l’héritage dans le contexte des types et de la programmation générale orientée objet, où les classes dérivées héritent des définitions de membre de leurs classes de base. Cette signification d’héritage s’applique également dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : les propriétés définies dans différentes classes de base sont exposées comme des attributs pour les classes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dérivées quand elles sont utilisées comme éléments et exposées sous forme de membres pour le code. L’héritage de la valeur de propriété concerne particulièrement la façon dont les valeurs de propriété peuvent hériter d’un élément à l’autre en fonction des relations parent-enfant dans une arborescence d’éléments. Cette arborescence d’éléments est plus directement visible quand des éléments sont imbriqués dans d’autres éléments à mesure que vous définissez des applications dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Les arborescences d’objets peuvent également être créées par programmation en ajoutant des objets aux collections désignées d’autres objets, et l’héritage de la valeur de propriété fonctionne de la même façon dans l’arborescence terminée au moment de l’exécution.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Applications pratiques de l’héritage de la valeur de propriété  
 Les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API incluent plusieurs propriétés pour lesquelles l’héritage de propriété est activé. En règle générale, il s’agit d’une propriété définie une seule fois par page, mais quand elle est également membre d’une des classes d’élément de base, elle existe aussi sur la plupart des éléments enfants. Par exemple, la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété contrôle la direction dans laquelle le contenu passé doit être présenté et réorganisé sur la page. En règle générale, vous voulez que le flux de texte soit traité de manière cohérente dans l’ensemble des éléments enfants. Si la direction du flux est redéfinie à un certain niveau de l’arborescence d’éléments par l’utilisateur ou une action de l’environnement, elle est redéfinie partout. Lorsque la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété est définie pour hériter, la valeur doit être définie ou réinitialisée une seule fois au niveau de l’arborescence d’éléments qui englobe les besoins de présentation de chaque page de l’application. Même la valeur par défaut initiale hérite de cette manière. Le modèle d’héritage de la valeur de propriété permet toujours aux éléments individuels de redéfinir la valeur dans les rares cas où un mélange de directions de flux est intentionnel.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Transformer une propriété personnalisée en propriété héritable  
 En changeant les métadonnées d’une propriété personnalisée, vous pouvez rendre héritables vos propres propriétés personnalisées. Toutefois, notez qu’une propriété désignée comme héritable a un impact sur les performances. Dans les cas où cette propriété n’a pas de valeur locale établie ou a une valeur obtenue par le biais de styles, de modèles ou d’une liaison de données, une propriété héritable transmet ses valeurs de propriété à tous les éléments enfants dans l’arborescence logique.  
  
 Pour qu’une propriété participe à l’héritage de valeur, créez une propriété jointe, comme décrit dans [Enregistrer une propriété jointe](how-to-register-an-attached-property.md). Inscrivez la propriété avec des métadonnées (<xref:System.Windows.FrameworkPropertyMetadata>) et spécifiez l’option «Inherits» dans les paramètres d’options de ces métadonnées. Vérifiez aussi que la propriété a une valeur par défaut établie, car cette valeur hérite désormais. Même si vous avez enregistré la propriété comme propriété jointe, vous pouvez aussi créer un « wrapper » de propriété pour un avoir accès get/set sur le type de propriétaire, comme pour les propriétés de dépendance « non jointes ». Après cela, la propriété pouvant être héritée peut être définie à l’aide du wrapper de propriété directe sur le type de propriétaire ou des types dérivés, ou elle peut être définie à l’aide <xref:System.Windows.DependencyObject>de la syntaxe de propriété jointe sur any.  
  
 Les propriétés jointes sont conceptuellement similaires aux propriétés globales; vous pouvez rechercher la valeur sur Any <xref:System.Windows.DependencyObject> et obtenir un résultat valide. Le scénario classique pour les propriétés jointes consiste à définir des valeurs de propriété sur les éléments enfants. ce scénario est plus efficace si la propriété en question est une propriété jointe qui est toujours implicitement présente en tant que propriété jointe sur chaque élément (<xref:System.Windows.DependencyObject>) dans l’arborescence.  
  
> [!NOTE]
> Même si l’héritage de la valeur de propriété peut sembler fonctionner pour les propriétés de dépendance non jointes, le comportement de l’héritage d’une propriété non jointe au-delà de certaines limites d’éléments dans l’arborescence d’exécution n’est pas défini. Utilisez <xref:System.Windows.DependencyProperty.RegisterAttached%2A> toujours pour enregistrer les propriétés où vous <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> spécifiez dans les métadonnées.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Héritage de valeurs de propriété au-delà des limites d’arborescence  
 L’héritage des propriétés fonctionne sur une arborescence d’éléments. Cette arborescence est souvent parallèle à l’arborescence logique. Toutefois, chaque fois que vous incluez un objet de niveau principal WPF dans le balisage qui définit une arborescence d' <xref:System.Windows.Media.Brush>éléments, telle que, vous avez créé une arborescence logique discontinue. Une arborescence logique vraie ne s’étend <xref:System.Windows.Media.Brush>pas conceptuellement au, car l’arborescence logique est un concept de niveau Framework WPF. Vous pouvez voir que cela est reflété dans les résultats lors de l' <xref:System.Windows.LogicalTreeHelper>utilisation des méthodes de. Toutefois, l’héritage de la valeur de propriété peut combler cet écart dans l’arborescence logique et peut toujours passer des valeurs héritées via, tant que la propriété héritable a été inscrite comme propriété jointe et qu’aucune limite de blocage d’héritage délibérée (telle que <xref:System.Windows.Controls.Frame>) est rencontré.  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d'ensemble des propriétés jointes](attached-properties-overview.md)
- [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md)
