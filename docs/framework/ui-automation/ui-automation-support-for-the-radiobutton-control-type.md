---
title: Prise en charge d'UI Automation pour le type de contrôle RadioButton
description: Obtenir des informations sur la prise en charge d’UI Automation pour le type de contrôle RadioButton. Découvrez l’arborescence, les propriétés, les modèles de contrôle et les événements requis.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Radio Button
- UI Automation, Radio Button control type
- RadioButton control type
ms.assetid: 87170464-7857-41f1-bcf7-bb41be31cb53
ms.openlocfilehash: cece51c864108bc54eb5e3350da3198a19646476
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281766"
---
# <a name="ui-automation-support-for-the-radiobutton-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle RadioButton

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle RadioButton. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Une case d’option se compose d’un bouton rond et d’un texte défini par l’application (étiquette), d’une icône ou d’une image bitmap qui indique un choix que l’utilisateur peut faire en sélectionnant le bouton. Une application utilise généralement des cases d’option dans une zone de groupe pour permettre à l’utilisateur de choisir parmi un ensemble d’options connexes mais s’excluant mutuellement. Par exemple, l’application peut présenter un groupe de cases d’option parmi lesquelles l’utilisateur peut sélectionner une préférence de format pour le texte sélectionné dans la zone cliente. L’utilisateur peut sélectionner un format aligné à gauche, aligné à droite ou centré en cochant la case d’option correspondante. En règle générale, l’utilisateur peut sélectionner une seule option à la fois parmi un ensemble de cases d’option.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requis pour le type de contrôle RadioButton. Les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spécifications s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 ou Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  

 Le tableau suivant illustre la vue de contrôle et la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de case d’option, et décrit ce que peut contenir chaque vue. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|RadioButton|RadioButton|  
  
 Aucun enfant ne figure dans la vue de contrôle ni dans la vue de contenu.  
  
<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  

 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour le type de contrôle RadioButton. Pour plus d’informations sur les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriétés, consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les remarques.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les remarques.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les remarques.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les remarques.|Le nom du contrôle de case d’option est le texte qui s’affiche en regard du bouton qui maintient l’état de sélection.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les remarques.|Le point interactif d’un contrôle de case d’option DOIT être un point qui définit la sélection sur la case d’option si l’utilisateur clique dessus avec le pointeur de souris.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les cases d’option sont des contrôles à étiquetage automatique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|RadioButton|Cette valeur est la même pour toutes les infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« case d’option »|Chaîne localisée correspondant au type de contrôle RadioButton.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle de case d’option est toujours inclus dans la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle de case d’option est toujours inclus dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  

 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de case d’option. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle / Propriété de modèle de contrôle|Prise en charge/valeur|Remarques|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Oui|Tous les contrôles de case d’option doivent prendre en charge le modèle Selection Item qui permet de les sélectionner.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Consultez les remarques.|La propriété `SelectionContainerProperty` doit toujours être définie afin qu’un client UI Automation puisse déterminer quelles autres cases d’option dans un contexte spécifique se rapportent les unes aux autres.  Pour la version Win32 de la case d’option, cette propriété n’est pas prise en charge, car il n’est pas possible d’obtenir ces informations à partir de cette infrastructure héritée.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Jamais|La case d’option ne peut pas passer d’un état à un autre une fois qu’elle a été définie.  Ce modèle ne doit jamais être pris en charge sur la case d’option.|  
  
<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  

 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de case d’option. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Support|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Jamais|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|None|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|None|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.RadioButton>
- [Vue d'ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
