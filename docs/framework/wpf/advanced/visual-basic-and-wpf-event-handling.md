---
title: Gérer les événements dans Visual Basic
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 959ef66f41f6c5f06e18a202109fba058c522d1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735410"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Gestion des événements Visual Basic et WPF
Pour le langage Microsoft Visual Basic .NET, vous pouvez utiliser le mot clé `Handles` spécifique au langage pour associer des gestionnaires d’événements à des instances, au lieu d’attacher des gestionnaires d’événements à des attributs ou à l’aide de la méthode <xref:System.Windows.UIElement.AddHandler%2A>. La technique `Handles` présente toutefois quelques limitations, car la syntaxe de `Handles` ne prend pas en charge certaines fonctionnalités d’événement routé spécifiques du système d’événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="using-handles-in-a-wpf-application"></a>Utilisation de « handles » dans une application WPF  
 Les gestionnaires d’événements connectés à des instances et à des événements par le biais de `Handles` doivent être définis dans la déclaration de classe partielle de l’instance. C’est également le cas des gestionnaires d’événements assignés par le biais de valeurs d’attribut sur les éléments. Vous pouvez uniquement spécifier `Handles` pour un élément de la page qui a une valeur de propriété <xref:System.Windows.FrameworkContentElement.Name%2A> (ou une [directive x :Name](../../../desktop-wpf/xaml-services/xname-directive.md) déclarée). Cela est dû au fait que la <xref:System.Windows.FrameworkContentElement.Name%2A> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] crée la référence d’instance qui est nécessaire pour prendre en charge le format de référence d' *instance. Event* requis par la syntaxe de `Handles`. Le seul élément qui peut être utilisé pour `Handles` sans référence <xref:System.Windows.FrameworkContentElement.Name%2A> est l’instance de l’élément racine qui définit la classe partielle.  
  
 Vous pouvez assigner le même gestionnaire à plusieurs éléments en séparant les références *Instance.Event* après `Handles` par des virgules.  
  
 Vous pouvez utiliser `Handles` pour assigner plusieurs gestionnaires à la même référence *Instance.Event*. Ne vous préoccupez pas de l’ordre dans lequel les gestionnaires sont introduits dans la référence `Handles` ; considérez que les gestionnaires qui gèrent le même événement peuvent être appelés dans n’importe quel ordre.  
  
 Pour supprimer un gestionnaire qui a été ajouté avec `Handles` dans la déclaration, vous pouvez appeler <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Vous pouvez utiliser `Handles` pour joindre des gestionnaires pour des événements routés, pour autant que vous joignez les gestionnaires à des instances qui définissent l’événement géré dans leurs tables de membres. Pour les événements routés, les gestionnaires attachés à `Handles` suivent les mêmes règles de routage que les gestionnaires associés en tant qu’attributs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou avec la signature commune de <xref:System.Windows.UIElement.AddHandler%2A>. Cela signifie que si l’événement est déjà marqué comme géré (la propriété <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d’événement est `True`), les gestionnaires attachés à `Handles` ne sont pas appelés en réponse à cette instance d’événement. L’événement peut être marqué comme géré par des gestionnaires d’instance sur un autre élément sur l’itinéraire, ou par la gestion de classe sur l’élément actuel ou sur des éléments antérieurs le long de l’itinéraire. Dans le cas d’événements d’entrée prenant en charge des événements de tunneling/propagation couplés, il est possible que l’itinéraire de tunneling ait marqué la paire d’événements comme gérée. Pour plus d’informations sur les événements routés, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Limitations de « Handles » dans le cadre de l’ajout de gestionnaires  
 `Handles` ne peut pas référencer de gestionnaires pour des événements attachés. Vous devez utiliser la méthode d’accesseur `add` pour cet événement attaché ou des attributs d’événement *nom_type.nom_événement* en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Pour plus d’informations, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
 Pour les événements routés, vous pouvez uniquement utiliser `Handles` pour assigner des gestionnaires aux instances où cet événement apparaît dans la table de membres. Dans le cas des événements routés en général, un élément parent peut toutefois jouer le rôle d’écouteur pour un événement des éléments enfants, même si ce dernier ne figure pas dans la table de membres de l’événement parent. Dans la syntaxe d’attribut, vous pouvez spécifier cela à l’aide d’une forme d’attribut *nom_type.nom_événement* qui qualifie le type qui définit réellement l’événement que vous souhaitez gérer. Par exemple, un `Page` parent (sans événement de `Click` défini) peut écouter des événements de clic de bouton en affectant un gestionnaire d’attributs sous la forme `Button.Click`. `Handles` ne prend cependant pas en charge le format *nom_type.nom_événement*, car il doit prendre en charge un format *instance.événement* incompatible. Pour plus d’informations, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
 `Handles` ne peut pas joindre des gestionnaires appelés pour des événements déjà marqués comme gérés. Au lieu de cela, vous devez utiliser le code et appeler la surcharge `handledEventsToo` de <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
> N’utilisez pas la syntaxe `Handles` dans Visual Basic code lorsque vous spécifiez un gestionnaire d’événements pour le même événement en XAML. Dans ce cas, le gestionnaire d’événements est appelé deux fois.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Implémentation de la fonctionnalité « Handles » par WPF  
 Quand une page [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] est compilée, le fichier intermédiaire déclare `Friend` `WithEvents` des références à chaque élément de la page qui a un jeu de propriétés <xref:System.Windows.FrameworkContentElement.Name%2A> (ou une [directive x :Name](../../../desktop-wpf/xaml-services/xname-directive.md) déclarée). Chaque instance nommée est un élément susceptible d’être assigné à un gestionnaire par le biais de `Handles`.  
  
> [!NOTE]
> Dans Visual Studio, IntelliSense peut vous montrer l’achèvement des éléments disponibles pour une référence `Handles` dans une page. Une étape de compilation peut toutefois s’avérer nécessaire pour permettre au fichier intermédiaire de remplir toutes les références `Friends`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md)
- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
