---
title: Prise en charge d'UI Automation pour le type de contrôle ToolTip
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
ms.openlocfilehash: ce1a3fa79c9e0074b3e0f7bfe5aa316fd0d28426
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785723"
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle ToolTip
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle ToolTip. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Les contrôles d’info-bulle sont des fenêtres contextuelles qui contiennent du texte.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle ToolTip. Les exigences de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles d’info-bulle, qu’il s’agisse [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 ou Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’info-bulle, et décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|Info-bulle<br /><br /> -Text (0 ou plus)<br />-Image (0 ou plus)|Info-bulle|  
  
 Les contrôles d’info-bulle apparaissent uniquement dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’ils peuvent recevoir le focus clavier. Sinon, toutes les informations de l’info-bulle sont disponibles à partir de la propriété `HelpTextProperty` sur l’élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] auquel l’info-bulle fait référence.  
  
 Les info-bulles doivent apparaître sous le contrôle auquel leurs informations font référence. Les clients doivent écouter `ToolTipOpenedEvent` pour s’assurer d’obtenir constamment les informations contenues dans les info-bulles.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles d’info-bulle. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|Remarques|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les remarques.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les remarques.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les remarques.|La zone interactive doit être la partie de l’info-bulle qui va masquer le contrôle. Certaines info-bulles n’ont pas cette possibilité et n’ont pas de zone interactive.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les remarques.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les remarques.|Le nom du contrôle d’info-bulle est le texte affiché dans l’info-bulle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les contrôles d’info-bulle sont toujours étiquetés automatiquement par leur contenu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Info-bulle|Cette valeur est identique pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« info-bulle »|Chaîne localisée correspondant au type de contrôle ToolTip.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Selon le cas|Si le contrôle d’info-bulle peut recevoir le focus clavier, il doit figurer dans l’affichage de contenu de l’arborescence. S’il s’agit uniquement de texte, il est disponible en tant que HelpTextProperty à partir du contrôle qui l’a déclenché.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle d’info-bulle doit toujours être un contrôle.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles d’info-bulle. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Prise en charge de|Remarques|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Selon le cas|Les info-bulles qui peuvent être fermées en cliquant sur un élément d’interface utilisateur doivent prendre en charge WindowPattern pour pouvoir se fermer automatiquement.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Selon le cas|Pour une meilleure accessibilité, un contrôle d’info-bulle peut prendre en charge le modèle de contrôle Text, bien que ce ne soit pas obligatoire. Le modèle de contrôle Text est utile quand le texte possède un style complexe et des attributs (par exemple, couleur, gras et italique).|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Les contrôles d’info-bulle doivent déclencher `ToolTipOpenedEvent` quand ils s’affichent à l’écran. L’événement inclut une référence à l’élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de l’info-bulle elle-même.  
  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’info-bulle. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge de|Remarques|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.ToolTip>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
