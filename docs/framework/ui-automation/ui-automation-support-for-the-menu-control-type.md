---
title: Prise en charge d'UI Automation pour le type de contrôle Menu
description: Obtenir des informations sur la prise en charge d’UI Automation pour le type de contrôle Menu. Découvrez l’arborescence, les propriétés, les modèles de contrôle et les événements requis.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: 2d9448f0a12ab5f4eb014731f74162adb8a539fa
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166069"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Menu
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour le type de contrôle Menu. Elle décrit l’arborescence [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] du contrôle et fournit les propriétés et les modèles de contrôle pour des scénarios de contrôle spécifiques.  
  
 Un contrôle menu permet une organisation hiérarchique des éléments associés à des commandes et des gestionnaires d’événements. Dans une application Microsoft Windows classique, une barre de menus contient plusieurs boutons de menu (tels que **fichier**, **Edition**et **fenêtre**) et chaque bouton de menu affiche un menu. Un menu contient un groupe d’éléments de menu (tels que **Nouveau**, **Ouvrir**et **Fermer**), qui peuvent être développés pour afficher des éléments de menu supplémentaires ou pour exécuter une action spécifique quand vous cliquez dessus.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle Menu. Les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spécifications s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 ou Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] concernant les contrôles menu et décrit ce que chaque affichage peut contenir. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|Menu<br /><br /> -MenuItem (1 ou plusieurs)|Non applicable (à moins que le contrôle de menu soit un menu contextuel parent d’un objet qui n’est pas un élément de menu)<br /><br /> -MenuItem (1 ou plusieurs)|  
  
 Les contrôles menu apparaissent toujours dans l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Les types de contrôle menu doivent apparaître sous le contrôle auquel leurs informations font référence. Les clients UI Automation doivent écouter `MenuOpenedEvent` pour faire en sorte d’obtenir constamment les informations communiquées par les contrôles menu. Les contrôles de menu contextuel constituent un cas particulier. Ils apparaissent en tant qu’enfants du Bureau.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement adaptée au type de contrôle Menu. Pour plus d’informations sur les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriétés, consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Non pris en charge|Avec le contrôle menu, il n’est pas nécessaire de définir une propriété Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Aucune étiquette n’est censée accompagner un contrôle menu standard.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Cette valeur est identique pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Le contrôle menu n’est pas inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle menu est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Il n’existe aucun modèle de contrôle obligatoire pour le type de contrôle Menu.  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Les contrôles menu doivent déclencher `MenuOpenedEvent` quand ils s’affichent à l’écran. `MenuOpenedEvent` comprend le texte du contrôle. `MenuClosedEvent` doit être déclenché quand un menu disparaît de l’écran.  
  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles menu. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge/valeur|Notes|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|None|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Menu>
- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Vue d'ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
