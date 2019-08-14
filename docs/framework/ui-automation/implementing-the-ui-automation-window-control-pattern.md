---
title: Implémentation du modèle de contrôle Window d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: 1d40b133beb68c14e7392139bf0753cedb67a4ef
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971819"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implémentation du modèle de contrôle Window d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente des conventions et des directives pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>, notamment des informations sur les propriétés, méthodes et événements <xref:System.Windows.Automation.WindowPattern> . Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le <xref:System.Windows.Automation.WindowPattern> modèle de contrôle est utilisé pour prendre en charge des contrôles qui fournissent des fonctionnalités fondamentales basées sur les fenêtres dans une interface graphique utilisateur (GUI) traditionnelle. Voici des exemples de contrôles qui doivent implémenter ce modèle de contrôle: les fenêtres d’application de niveau supérieur, les fenêtres enfants de l’interface multidocument (MDI), les contrôles de volet de fractionnement redimensionnables, les boîtes de dialogue modales et les fenêtres d’aide de bulle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
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
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Événement|Aucun|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Événement|Aucun|  
|<xref:System.Windows.Automation.WindowInteractionState>|Événement|N’est pas nécessairement défini sur <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -Lorsqu’un contrôle ne prend pas en charge un comportement demandé.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Lorsque le paramètre n’est pas un nombre valide.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
