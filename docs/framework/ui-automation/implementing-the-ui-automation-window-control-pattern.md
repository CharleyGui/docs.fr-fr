---
title: Implémentation du modèle de contrôle Window d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: d8afaa13bd4eca9f9fcd4c8ed26c09c62ad74931
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447031"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implémentation du modèle de contrôle Window d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente des conventions et des directives pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>, notamment des informations sur les propriétés, méthodes et événements <xref:System.Windows.Automation.WindowPattern> . Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI). Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Window, notez les conventions et recommandations suivantes :  
  
- Pour prendre en charge la possibilité de modifier la taille de la fenêtre et la position de l’écran à l’aide d’UI Automation, un contrôle doit implémenter <xref:System.Windows.Automation.Provider.ITransformProvider> en plus de <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Les contrôles qui contiennent des barres de titre et des éléments de barre de titre qui permettent de déplacer, redimensionner, agrandir, réduire ou fermer le contrôle sont généralement obligatoires pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- En général, les contrôles tels que les info-bulles contextuelles, les zones de liste modifiable ou les menus déroulants n’implémentent pas <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Les fenêtres d’info-bulle se distinguent des info-bulles contextuelles de base par un bouton Fermer identique à celui des fenêtres.  
  
- Le mode plein écran n’est pas pris en charge par IWindowProvider, car il est propre à la fonctionnalité d’une application et n’est pas un comportement standard de fenêtre.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Membres obligatoires pour IWindowProvider  
 Les propriétés, méthodes et événements suivants sont obligatoires pour l’interface IWindowProvider.  
  
|Membre obligatoire|Type de membre|Notes|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Property|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Méthode|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Méthode|aucune.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Méthode|aucune.|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|événement|aucune.|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|événement|aucune.|  
|<xref:System.Windows.Automation.WindowInteractionState>|événement|N’est pas nécessairement défini sur <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -   When a control does not support a requested behavior.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -   When the parameter is not a valid number.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Présentation de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
