---
title: Événements de la durée de vie d'un objet
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141105"
---
# <a name="object-lifetime-events"></a>Événements de la durée de vie d'un objet
Cette rubrique décrit les événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spécifiques qui correspondent aux étapes de la durée de vie de création, d’utilisation et de destruction d’un objet.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique part du principe que vous maîtrisez les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], et que vous avez lu la rubrique [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour pouvoir suivre les exemples de cette rubrique, vous devez aussi maîtriser le langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (consultez [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>Événements de la durée de vie d'un objet  
 Tous les objets du code géré Microsoft .NET Framework passent par un ensemble similaire d’étapes de la vie, de la création, de l’utilisation et de la destruction. De nombreux objets passent aussi par une étape de fin de vie qui se produit pendant la phase de destruction. Les objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus précisément les objets visuels que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifie comme des éléments, ont aussi un ensemble d’étapes communes de vie d’objet. Les modèles de programmation et d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exposent ces étapes comme une série d’événements. Il existe quatre types d’objet principaux dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en ce qui concerne les événements de durée de vie : éléments en général, éléments de fenêtre, hôtes de navigation et objets d’application. Les fenêtres et les hôtes de navigation appartiennent aussi au groupe d’objets visuels (éléments) le plus grand. Cette rubrique décrit les événements de durée de vie communs à tous les éléments et présente les événements plus spécifiques qui s’appliquent aux définitions d’application, fenêtres ou hôtes de navigation.  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>Événements de durée de vie communs des éléments  
 Tout élément de niveau cadre WPF (ces <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>objets dérivés de <xref:System.Windows.FrameworkElement.Initialized>l’un ou l’autre ou ) a trois événements communs à vie: , <xref:System.Windows.FrameworkElement.Loaded>, et <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Initialized  
 <xref:System.Windows.FrameworkElement.Initialized>est soulevé en premier, et correspond approximativement à l’initialisation de l’objet par l’appel à son constructeur. Comme l’événement se produit en réponse à l’initialisation, vous êtes assuré que toutes les propriétés de l’objet sont définies. (Une exception est l’utilisation d’expressions telles que les ressources dynamiques ou la liaison; ce seront des expressions non évaluées.) En raison de l’exigence selon laquelle toutes <xref:System.Windows.FrameworkElement.Initialized> les propriétés sont définies, la séquence d’être soulevée par des éléments imbriqués qui sont définis dans la majoration semble se produire dans l’ordre des éléments les plus profonds de l’arbre élément d’abord, puis des éléments parents vers la racine. Cet ordre s’explique par le fait que les relations parent-enfant et contenant-contenu sont des propriétés. Par conséquent, le parent ne peut pas signaler l’initialisation tant que les éléments enfants qui remplissent la propriété ne sont pas eux aussi complètement initialisés.  
  
 Lorsque vous écrivez des gestionnaires <xref:System.Windows.FrameworkElement.Initialized> en réponse à l’événement, vous devez considérer qu’il n’y a aucune garantie que tous les autres éléments de l’arbre élément (arbre logique ou arbre visuel) autour de l’endroit où le gestionnaire est attaché ont été créés, en particulier les éléments parentaux. Les variables membres peuvent avoir la valeur null ou les sources de données peuvent ne pas être encore remplies par la liaison sous-jacente (même au niveau de l’expression).  
  
### <a name="loaded"></a>Loaded  
 <xref:System.Windows.FrameworkElement.Loaded>est ensuite soulevée. L’événement <xref:System.Windows.FrameworkElement.Loaded> est soulevé avant le rendu final, mais après que le système de mise en page a calculé toutes les valeurs nécessaires pour le rendu. <xref:System.Windows.FrameworkElement.Loaded>implique que l’arbre logique dans lequel un élément est contenu est complet et se connecte à une source de présentation qui fournit le HWND et la surface de rendu. La liaison de données standard (liaison aux sources locales, telles que <xref:System.Windows.FrameworkElement.Loaded>d’autres propriétés ou sources de données directement définies) aura eu lieu avant . La liaison de données asynchrone (sources externes ou dynamiques) peut s’être produite, mais du fait même de sa nature asynchrone, elle peut ne pas avoir eu lieu.  
  
 Le mécanisme par <xref:System.Windows.FrameworkElement.Loaded> lequel l’événement <xref:System.Windows.FrameworkElement.Initialized>est soulevé est différent de . L’événement <xref:System.Windows.FrameworkElement.Initialized> est soulevé élément par élément, sans coordination directe par un arbre d’élément complété. En revanche, <xref:System.Windows.FrameworkElement.Loaded> l’événement est soulevé comme un effort coordonné à travers l’arbre élément entier (en particulier, l’arbre logique). Lorsque tous les éléments de l’arbre sont dans <xref:System.Windows.FrameworkElement.Loaded> un état où ils sont considérés comme chargés, l’événement est d’abord soulevé sur l’élément racine. L’événement <xref:System.Windows.FrameworkElement.Loaded> est ensuite soulevé successivement sur chaque élément enfant.  
  
> [!NOTE]
> Ce comportement peut rappeler en apparence le tunneling dans le cas d’un événement routé. Cependant, aucune information n’est transmise d’un événement à l’autre. Chaque élément a toujours la <xref:System.Windows.FrameworkElement.Loaded> possibilité de gérer son événement, et le marquage des données de l’événement tel qu’il est traité n’a aucun effet au-delà de cet élément.  
  
### <a name="unloaded"></a>Unloaded  
 <xref:System.Windows.FrameworkElement.Unloaded>est soulevée en dernier et est initiée soit par la source de présentation ou le parent visuel étant enlevé. Lorsqu’il <xref:System.Windows.FrameworkElement.Unloaded> est soulevé et manipulé, l’élément qui <xref:System.Windows.FrameworkElement.Parent%2A> est le parent source de l’événement (tel que déterminé par la propriété) ou tout élément donné vers le haut dans les arbres logiques ou visuels peut avoir déjà été non réglé, ce qui signifie que la liaison des données, les références de ressources, et les styles peuvent ne pas être réglés à leur valeur normale ou dernière heure de fonctionnement connue.  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>Éléments de modèle d’application d’événements de durée de vie  
 S’appuyant sur les événements communs à vie <xref:System.Windows.Application> <xref:System.Windows.Window>pour <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>les éléments sont les éléments suivants modèle d’application: , , , et <xref:System.Windows.Controls.Frame>. Ces éléments étendent les événements de durée de vie communs avec des événements supplémentaires en rapport avec leur fonction. Ils sont décrits en détail aux emplacements suivants :  
  
- <xref:System.Windows.Application>: [Aperçu de la gestion des applications](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [WPF Windows Overview](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>et : [Aperçu de la navigation](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Priorité de la valeur de la propriété de dépendance](dependency-property-value-precedence.md)
- [Vue d'ensemble des événements routés](routed-events-overview.md)
