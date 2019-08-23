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
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933488"
---
# <a name="object-lifetime-events"></a>Événements de la durée de vie d'un objet
Cette rubrique décrit les événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spécifiques qui correspondent aux étapes de la durée de vie de création, d’utilisation et de destruction d’un objet.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous maîtrisez les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], et que vous avez lu la rubrique [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour pouvoir suivre les exemples de cette rubrique, vous devez aussi maîtriser le langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (consultez [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)) et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Événements de la durée de vie d'un objet  
 Tous les objets dans Microsoft .NET code managé du Framework passent par un ensemble similaire de phases de vie, de création, d’utilisation et de destruction. De nombreux objets passent aussi par une étape de fin de vie qui se produit pendant la phase de destruction. Les objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus précisément les objets visuels que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifie comme des éléments, ont aussi un ensemble d’étapes communes de vie d’objet. Les modèles de programmation et d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exposent ces étapes comme une série d’événements. Il existe quatre types d’objet principaux dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en ce qui concerne les événements de durée de vie : éléments en général, éléments de fenêtre, hôtes de navigation et objets d’application. Les fenêtres et les hôtes de navigation appartiennent aussi au groupe d’objets visuels (éléments) le plus grand. Cette rubrique décrit les événements de durée de vie communs à tous les éléments et présente les événements plus spécifiques qui s’appliquent aux définitions d’application, fenêtres ou hôtes de navigation.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Événements de durée de vie communs des éléments  
 Tout élément de niveau infrastructure WPF (ces objets dérivant de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) a trois événements de durée de vie communs <xref:System.Windows.FrameworkElement.Initialized>: <xref:System.Windows.FrameworkElement.Loaded>, et <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Initialized  
 <xref:System.Windows.FrameworkElement.Initialized>est déclenché en premier, et correspond approximativement à l’initialisation de l’objet par l’appel à son constructeur. Comme l’événement se produit en réponse à l’initialisation, vous êtes assuré que toutes les propriétés de l’objet sont définies. (Il existe une exception pour les utilisations d’expressions, telles que les ressources dynamiques ou la liaison ; ces expressions ne sont pas évaluées.) En raison de la nécessité de définir toutes les propriétés, la séquence de <xref:System.Windows.FrameworkElement.Initialized> levée par les éléments imbriqués définis dans le balisage semble se produire dans l’ordre des éléments les plus profonds de l’arborescence d’éléments, puis dans les éléments parents vers la racine. Cet ordre s’explique par le fait que les relations parent-enfant et contenant-contenu sont des propriétés. Par conséquent, le parent ne peut pas signaler l’initialisation tant que les éléments enfants qui remplissent la propriété ne sont pas eux aussi complètement initialisés.  
  
 Lorsque vous écrivez des gestionnaires en réponse à l’événement <xref:System.Windows.FrameworkElement.Initialized> , vous devez tenir compte du fait qu’il n’y a aucune garantie que tous les autres éléments de l’arborescence d’éléments (arborescence logique ou arborescence d’éléments visuels) autour de l’emplacement auquel le gestionnaire est attaché ont été créés, en particulier éléments parents. Les variables membres peuvent avoir la valeur null ou les sources de données peuvent ne pas être encore remplies par la liaison sous-jacente (même au niveau de l’expression).  
  
### <a name="loaded"></a>Chargé  
 <xref:System.Windows.FrameworkElement.Loaded>est déclenché suivant. L' <xref:System.Windows.FrameworkElement.Loaded> événement est déclenché avant le rendu final, mais une fois que le système de disposition a calculé toutes les valeurs nécessaires pour le rendu. <xref:System.Windows.FrameworkElement.Loaded>implique que l’arborescence logique dans laquelle un élément est contenu est terminée et se connecte à une source de présentation qui fournit le HWND et la surface de rendu. La liaison de données standard (liaison à des sources locales, telles que d’autres propriétés ou des sources de données directement définies <xref:System.Windows.FrameworkElement.Loaded>) s’est produite avant. La liaison de données asynchrone (sources externes ou dynamiques) peut s’être produite, mais du fait même de sa nature asynchrone, elle peut ne pas avoir eu lieu.  
  
 Le mécanisme par lequel l' <xref:System.Windows.FrameworkElement.Loaded> événement est déclenché est différent de <xref:System.Windows.FrameworkElement.Initialized>. L' <xref:System.Windows.FrameworkElement.Initialized> événement est déclenché élément par élément, sans coordination directe par une arborescence d’éléments terminée. En revanche, l' <xref:System.Windows.FrameworkElement.Loaded> événement est déclenché comme un effort coordonné dans toute l’arborescence d’éléments (plus précisément, l’arborescence logique). Lorsque tous les éléments de l’arborescence se trouvent dans un État dans lequel ils sont considérés comme étant chargés, l' <xref:System.Windows.FrameworkElement.Loaded> événement est déclenché pour la première fois sur l’élément racine. L' <xref:System.Windows.FrameworkElement.Loaded> événement est ensuite déclenché successivement sur chaque élément enfant.  
  
> [!NOTE]
> Ce comportement peut rappeler en apparence le tunneling dans le cas d’un événement routé. Cependant, aucune information n’est transmise d’un événement à l’autre. Chaque élément a toujours la possibilité de gérer son <xref:System.Windows.FrameworkElement.Loaded> événement et le marquage des données d’événement comme étant gérées n’a aucun effet au-delà de cet élément.  
  
### <a name="unloaded"></a>Non chargé  
 <xref:System.Windows.FrameworkElement.Unloaded>est déclenché en dernier et est initié par la source de présentation ou le parent visuel en cours de suppression. Lorsque <xref:System.Windows.FrameworkElement.Unloaded> est déclenché et géré, l’élément qui est le parent de la source de l’événement <xref:System.Windows.FrameworkElement.Parent%2A> (tel que déterminé par la propriété) ou tout élément donné vers le haut dans les arborescences logiques ou visuelles a peut-être déjà été désactivé, ce qui signifie que la liaison de données, les références de ressources , et les styles ne peuvent pas être définis sur leur valeur d’exécution normale ou la dernière valeur connue.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Éléments de modèle d’application d’événements de durée de vie  
 L’élaboration des événements de durée de vie courants pour les éléments est l’un <xref:System.Windows.Application>des éléments de <xref:System.Windows.Navigation.NavigationWindow>modèle d' <xref:System.Windows.Controls.Frame>application suivants:, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, et. Ces éléments étendent les événements de durée de vie communs avec des événements supplémentaires en rapport avec leur fonction. Ils sont décrits en détail aux emplacements suivants :  
  
- <xref:System.Windows.Application>: [Vue d’ensemble](../app-development/application-management-overview.md)de la gestion des applications.  
  
- <xref:System.Windows.Window>: [Vue d’ensemble de Windows WPF](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>et :<xref:System.Windows.Controls.Frame> [Vue d’ensemble](../app-development/navigation-overview.md)de la navigation.  
  
## <a name="see-also"></a>Voir aussi

- [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md)
- [Vue d’ensemble des événements routés](routed-events-overview.md)
