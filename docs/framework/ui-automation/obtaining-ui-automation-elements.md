---
title: Obtention d'éléments UI Automation
description: Passez en revue les différentes façons d’obtenir des objets AutomationElement (UI Automation Element) pour les éléments de l’interface utilisateur.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 2b741dde3b30334ba8fa990d73044da7e3bdd2da
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168167"
---
# <a name="obtaining-ui-automation-elements"></a>Obtention d'éléments UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique décrit les différentes façons d’obtenir des objets <xref:System.Windows.Automation.AutomationElement> pour les éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
> [!CAUTION]
> Si votre application cliente peut tenter de rechercher des éléments dans sa propre interface utilisateur, vous devez effectuer tous les appels [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur un thread distinct. Pour plus d'informations, consultez [UI Automation Threading Issues](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Élément racine  
 Toutes les recherches d’objets <xref:System.Windows.Automation.AutomationElement> doivent avoir un point de départ. Cela peut être n’importe quel élément, y compris le bureau, une fenêtre d’application ou un contrôle.  
  
 L’élément racine pour le bureau, duquel tous les éléments proviennent, est obtenu à partir de la propriété <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> statique.  
  
> [!CAUTION]
> En général, vous devez essayer d’obtenir uniquement les enfants directs de <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Une recherche des descendants peut itérer au sein de centaines ou de milliers d’éléments, ce qui peut provoquer un dépassement de capacité de la pile. Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Conditions  
 Pour la plupart des techniques que vous pouvez utiliser pour récupérer des éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , vous devez spécifier un <xref:System.Windows.Automation.Condition>, qui est un ensemble de critères définissant les éléments que vous souhaitez récupérer.  
  
 La condition la plus simple est <xref:System.Windows.Automation.Condition.TrueCondition>, un objet prédéfini spécifiant que tous les éléments dans la zone de recherche doivent être retournés. La condition<xref:System.Windows.Automation.Condition.FalseCondition>, inverse de <xref:System.Windows.Automation.Condition.TrueCondition>, est moins utile, car elle empêche certains éléments d’être recherchés.  
  
 Trois autres conditions prédéfinies peuvent être utilisées seules ou combinées à d’autres conditions : <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>et <xref:System.Windows.Automation.Automation.RawViewCondition>. La condition, utilisée par elle-même, est équivalente à , car elle ne filtre pas les éléments par leurs propriétés  ou  .  
  
 D’autres conditions sont développées à partir d’un ou plusieurs objets <xref:System.Windows.Automation.PropertyCondition> , chacun spécifiant une valeur de propriété. Par exemple, une condition <xref:System.Windows.Automation.PropertyCondition> peut spécifier que l’élément est activé ou qu’il prend en charge un certain modèle de contrôle.  
  
 Les conditions peuvent être combinées à l’aide d’une logique booléenne en construisant des objets de types <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>et <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Étendue de recherche  
 Les recherches effectuées à l’aide de <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A> doivent avoir une étendue et un point de départ.  
  
 L’étendue définit l’espace autour du point de départ dans lequel doit avoir lieu la recherche. Cela peut inclure l’élément lui-même, ses frères, son parent, ses ancêtres, ses enfants immédiats et ses descendants.  
  
 L’étendue d’une recherche est définie par une combinaison de valeurs au niveau du bit de l’énumération <xref:System.Windows.Automation.TreeScope> .  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Recherche d’un élément connu  
 Pour rechercher un élément connu, identifié par sa propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>ou une autre propriété ou combinaison de propriétés, il est plus facile d’utiliser la méthode <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> . Si l’élément recherché est une fenêtre d’application, le point de départ de la recherche peut être <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Cette façon de rechercher des éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] est particulièrement utile dans les scénarios de tests automatisés.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Recherche d’éléments dans une sous-arborescence  
 Pour rechercher tous les éléments répondant à des critères spécifiques liés à un élément connu, vous pouvez utiliser <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Par exemple, vous pouvez utiliser cette méthode pour récupérer des éléments de liste ou des éléments de menu d’une liste ou d’un menu, ou pour identifier tous les contrôles d’une boîte de dialogue.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Parcourir une sous-arborescence  
 Si vous ne connaissez pas au préalable les applications avec lesquelles votre client peut être utilisé, vous pouvez construire une sous-arborescence de tous les éléments d’intérêt à l’aide de la classe <xref:System.Windows.Automation.TreeWalker> . Votre application peut le faire en réponse à un événement de modification de focus, c’est-à-dire, quand une application ou un contrôle reçoit le focus d’entrée, le client UI Automation examine les enfants, voire tous les descendants de l’élément ayant le focus.  
  
 Une autre façon d’utiliser <xref:System.Windows.Automation.TreeWalker> est d’identifier les ancêtres d’un élément. Par exemple, en parcourant l’arborescence, vous pouvez identifier la fenêtre parente d’un contrôle.  
  
 Vous pouvez utiliser <xref:System.Windows.Automation.TreeWalker> en créant un objet de la classe (qui définit les éléments d’intérêt en passant une condition <xref:System.Windows.Automation.Condition>), ou à l’aide de l’un des objets prédéfinis suivants, définis en tant que champs de <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Recherche uniquement les éléments dont la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> est `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Recherche uniquement les éléments dont la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> est `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Recherche tous les éléments.|  
  
 Une fois que vous avez obtenu un <xref:System.Windows.Automation.TreeWalker>, son utilisation est simple. Appelez simplement les méthodes `Get` pour naviguer entre les éléments de la sous-arborescence.  
  
 La méthode <xref:System.Windows.Automation.TreeWalker.Normalize%2A> peut être utilisée pour naviguer vers un élément dans la sous-arborescence à partir d’un autre élément qui ne fait pas partie de l’affichage. Par exemple, supposons que vous avez créé un affichage d’une sous-arborescence à l’aide de <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Votre application reçoit une notification l’informant qu’une barre de défilement a reçu le focus d’entrée. Comme une barre de défilement n’est pas un élément de contenu, elle n’est pas présente dans l’affichage de la sous-arborescence. Toutefois, vous pouvez passer <xref:System.Windows.Automation.AutomationElement> qui représente la barre de défilement à <xref:System.Windows.Automation.TreeWalker.Normalize%2A> et récupérer l’ancêtre le plus proche qui se trouve dans l’affichage de contenu.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Autres moyens de récupérer un élément  
 Outre les recherches et la navigation, vous pouvez récupérer un <xref:System.Windows.Automation.AutomationElement> des façons suivantes.  
  
### <a name="from-an-event"></a>À partir d’un événement  
 Quand votre application reçoit un événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , l’objet source passé à votre gestionnaire d’événements est un <xref:System.Windows.Automation.AutomationElement>. Par exemple, si vous êtes abonné à des événements de changement de focus, la source passée à votre <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> est l’élément qui a reçu le focus.  
  
 Pour plus d'informations, consultez [Subscribe to UI Automation Events](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>À partir d’un point  
 Si vous disposez de coordonnées d’écran (par exemple, la position d’un curseur), vous pouvez récupérer un <xref:System.Windows.Automation.AutomationElement> à l’aide de la méthode statique <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> .  
  
### <a name="from-a-window-handle"></a>À partir d’un handle de fenêtre  
 Pour récupérer un <xref:System.Windows.Automation.AutomationElement> à partir d’un HWND, utilisez la méthode statique <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> .  
  
### <a name="from-the-focused-control"></a>À partir du contrôle ayant le focus  
 Vous pouvez récupérer un <xref:System.Windows.Automation.AutomationElement> qui représente le contrôle ayant le focus à partir de la propriété statique <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> .  
  
## <a name="see-also"></a>Voir aussi

- [Rechercher un élément UI Automation basé sur une condition de propriété](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Naviguer entre les éléments UI Automation avec TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Vue d’ensemble de l’arborescence UI Automation](ui-automation-tree-overview.md)
