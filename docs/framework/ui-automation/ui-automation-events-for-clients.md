---
title: Événements UI Automation pour les clients
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: b56fc09b33a846fe94a52e19dc4b9c806d79c121
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044106"
---
# <a name="ui-automation-events-for-clients"></a>Événements UI Automation pour les clients
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique décrit comment les événements [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sont utilisés par les clients UI Automation.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet aux clients de s’abonner à des événements d’intérêt. Cette fonctionnalité améliore les performances en éliminant le besoin d’interroger continuellement tous les éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] du système pour vérifier si des informations, la structure ou l’état ont été modifiés.  
  
 L’efficacité est également améliorée par la possibilité d’écouter des événements uniquement dans une portée définie. Par exemple, un client peut écouter des événements de modification de focus sur tous les éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de l’arborescence ou sur un seul élément et ses descendants.  
  
> [!NOTE]
> Ne supposez pas que tous les événements possibles sont déclenchés par un fournisseur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]. Par exemple, toutes les modifications de propriété n’entraînent pas nécessairement le déclenchement d’événements par les fournisseurs de proxys standard pour les contrôles [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].  
  
 Pour une vue d’ensemble plus [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] large des événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Les applications clientes s’abonnent à des événements d’un type particulier en inscrivant un gestionnaire d’événements, à l’aide de l’une des méthodes suivantes.  
  
|Méthode|Type d'événement|Type d'arguments d'événement|Type délégué|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Modification du focus|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Modification de propriété|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Modification de la structure|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tous les autres événements, identifiés par un <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> ou <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Avant d’appeler la méthode, vous devez créer une méthode déléguée pour gérer l’événement. Si vous préférez, vous pouvez gérer différents types d’événements dans une seule méthode et passer cette méthode dans plusieurs appels à l’une des méthodes du tableau. Par exemple, un seul <xref:System.Windows.Automation.AutomationEventHandler> peut être configuré pour gérer divers événements différemment en fonction de <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
> Pour traiter les événements de fermeture de fenêtre, effectuez un cast du type d’argument passé au gestionnaire d’événements en tant que <xref:System.Windows.Automation.WindowClosedEventArgs>. Étant donné que l’élément [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de la fenêtre n’est plus valide, vous ne pouvez pas utiliser le paramètre `sender` pour récupérer des informations. Utilisez plutôt <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A>.  
  
> [!CAUTION]
> Si votre application est susceptible de recevoir des événements de sa propre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], n’utilisez pas le thread d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de votre application pour vous abonner aux événements ou pour annuler l’abonnement. Cela peut entraîner un comportement imprévisible. Pour plus d'informations, consultez [UI Automation Threading Issues](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Lors de l’arrêt, ou quand des événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ne sont plus intéressants pour l’application, les clients UI Automation doivent appeler l’une des méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été inscrit à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été inscrit à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été inscrit à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Annule l’inscription de tous les gestionnaires d’événements inscrits.|  
  
 Pour obtenir un exemple de code, consultez [s’abonner à des événements UI Automation](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Voir aussi

- [S’abonner à des événements UI Automation](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
- [Vue d’ensemble des événements UI Automation](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Vue d’ensemble des propriétés UI Automation](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Exemple TrackFocus](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
