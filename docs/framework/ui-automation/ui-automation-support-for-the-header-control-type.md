---
title: Prise en charge d'UI Automation pour le type de contrôle Header
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Header control type
- Header control type
- control types, Header
ms.assetid: d2e48891-2dbe-409e-8655-2f753908e29b
ms.openlocfilehash: be812fd9063674cc82d62a8c0207e27f3543be3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179767"
---
# <a name="ui-automation-support-for-the-header-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Header
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle Header. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le contrôle header fournit un conteneur visuel pour les étiquettes des lignes ou colonnes d’informations.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requis pour le type de contrôle Header. Les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] exigences s’appliquent [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]à tous les contrôles d’en-tête, que ce soit, Win32, ou Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] concernant les contrôles header et décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|En-tête<br /><br /> - HeaderItem (1 ou plus)|None|  
  
 Les contrôles header ont toujours 1 ou plusieurs enfants dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Les contrôles header n’ont aucun enfant dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles header. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les remarques.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les remarques.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les remarques.|Pris en charge s’il existe un rectangle englobant. Si les points du rectangle englobant ne sont pas tous interactifs et que vous effectuez un test de positionnement spécialisé, vous devez remplacer et fournir un point interactif.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les remarques.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les remarques.|Le contrôle header a besoin d’un nom s’il existe plusieurs en-têtes de lignes ou plusieurs en-têtes de colonnes. Cela identifie les informations présentes dans l’en-tête.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`.|Les contrôles header n’ont pas d’étiquette statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|En-tête|Cette valeur est la même pour toutes les infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« en-tête »|Cette valeur est la même pour toutes les infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Horizontal|La valeur de cette propriété expose la position du contrôle header : en-tête de ligne ou en-tête de colonne.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Le contrôle header n’est pas inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle header est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles header. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Support|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Dépend|Implémentez ce modèle de contrôle si le contrôle header peut être redimensionné.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles header. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Support|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|Obligatoire|None|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Header>
- [Vue d'ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
