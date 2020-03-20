---
title: Implémentation du modèle de contrôle Window d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180034"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implémentation du modèle de contrôle Window d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente des conventions et des directives pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>, notamment des informations sur les propriétés, méthodes et événements <xref:System.Windows.Automation.WindowPattern> . Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le <xref:System.Windows.Automation.WindowPattern> modèle de commande est utilisé pour prendre en charge les contrôles qui fournissent des fonctionnalités fondamentales basées sur les fenêtres au sein d’une interface utilisateur graphique traditionnelle (GUI). Des exemples de contrôles qui doivent implémenter ce modèle de contrôle comprennent les fenêtres d’application de haut niveau, les fenêtres pour enfants à interface multi-documents (MDI), les commandes resizables de vitres fendues, les dialogues modaux et les fenêtres d’aide aux ballons.  
  
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
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Méthode|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Méthode|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Méthode|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Événement|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Événement|None|  
|<xref:System.Windows.Automation.WindowInteractionState>|Événement|N’est pas nécessairement défini sur <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - Lorsqu’un contrôle ne prend pas en charge un comportement demandé.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - Lorsque le paramètre n’est pas un numéro valide.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
