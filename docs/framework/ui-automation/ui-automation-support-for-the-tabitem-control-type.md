---
title: Prise en charge d'UI Automation pour le type de contrôle TabItem
ms.date: 03/30/2017
helpviewer_keywords:
- Tab Item control type
- control types, Tab Item
- UI Automation, Tab Item control type
ms.assetid: 9b21160d-e1c2-468b-9275-26e4369ae40d
ms.openlocfilehash: 480cab96f34b3f21e8d37c1262caa5217d356b72
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801748"
---
# <a name="ui-automation-support-for-the-tabitem-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle TabItem
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle TabItem. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Ces conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Un contrôle d’élément d’onglet est le contrôle dans un contrôle d’onglet qui permet de sélectionner une page spécifique à afficher dans une fenêtre.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires pour le type de contrôle TabItem. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles d’élément d’onglet, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation requise  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’élément d’onglet, et décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|TabItem<br /><br /> <ul><li>Image (0 ou 1)</li><li>Text</li><li>Volet<br /><br /> <ul><li>Plusieurs contrôles (0 ou plus)</li></ul></li></ul>|TabItem<br /><br /> <ul><li>Volet<br /><br /> <ul><li>Plusieurs contrôles (0 ou plus)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles d’élément d’onglet. Pour plus d’informations sur les propriétés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Voir les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Voir les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Voir les notes.|Le contrôle d’élément d’onglet doit avoir une zone interactive qui entraîne la sélection de l’élément.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Voir les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Voir les notes.|Le contrôle d’élément d’onglet est étiqueté automatiquement.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Le contrôle d’élément d’onglet n’a pas d’étiquette de texte statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TabItem|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« élément d’onglet »|Chaîne localisée correspondant à ce type de contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle d’élément d’onglet doit toujours être du contenu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle d’élément d’onglet doit toujours être un contrôle.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation requis  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles d’élément d’onglet. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Prise en charge de|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Oui|Le contrôle d’élément d’onglet doit prendre en charge SelectionItemPattern.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Non|Le contrôle d’élément d’onglet ne prend jamais en charge InvokePattern.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’élément d’onglet. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge de|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.TabItem>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
