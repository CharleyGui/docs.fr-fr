---
title: Prise en charge d'UI Automation pour le type de contrôle Menu
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: f9126c6531c564d0a6aebca5b1369cadf0b6f03b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954975"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Menu
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour le type de contrôle Menu. Elle décrit l’arborescence [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] du contrôle et fournit les propriétés et les modèles de contrôle pour des scénarios de contrôle spécifiques.  
  
 Un contrôle menu permet une organisation hiérarchique des éléments associés à des commandes et des gestionnaires d’événements. Dans une application [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] classique, une barre de menus contient plusieurs boutons de menu (tels que **Fichier**, **Edition**et **Fenêtre**) et chaque bouton de menu affiche un menu. Un menu contient un groupe d’éléments de menu (tels que **Nouveau**, **Ouvrir**et **Fermer**), qui peuvent être développés pour afficher des éléments de menu supplémentaires ou pour exécuter une action spécifique quand vous cliquez dessus.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle Menu. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles list, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] concernant les contrôles menu et décrit ce que chaque affichage peut contenir. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|Menu<br /><br /> -MenuItem (1 ou plusieurs)|Non applicable (à moins que le contrôle de menu soit un menu contextuel parent d’un objet qui n’est pas un élément de menu)<br /><br /> -MenuItem (1 ou plusieurs)|  
  
 Les contrôles menu apparaissent toujours dans l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Les types de contrôle menu doivent apparaître sous le contrôle auquel leurs informations font référence. Les clients UI Automation doivent écouter `MenuOpenedEvent` pour faire en sorte d’obtenir constamment les informations communiquées par les contrôles menu. Les contrôles de menu contextuel constituent un cas particulier. Ils apparaissent en tant qu’enfants du Bureau.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement adaptée au type de contrôle Menu. Pour plus d’informations [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur les propriétés, consultez [UI Automation Properties for clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Non prise en charge|Avec le contrôle menu, il n’est pas nécessaire de définir une propriété Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Aucune étiquette n’est censée accompagner un contrôle menu standard.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Cette valeur est identique pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Le contrôle menu n’est pas inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle menu est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Il n’existe aucun modèle de contrôle obligatoire pour le type de contrôle Menu.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Les contrôles menu doivent déclencher `MenuOpenedEvent` quand ils s’affichent à l’écran. `MenuOpenedEvent` comprend le texte du contrôle. `MenuClosedEvent` doit être déclenché quand un menu disparaît de l’écran.  
  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles menu. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge/valeur|Notes|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Menu>
- [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Vue d’ensemble des types de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](../../../docs/framework/ui-automation/ui-automation-overview.md)
