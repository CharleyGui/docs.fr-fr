---
title: Prise en charge d'UI Automation pour le type de contrôle RadioButton
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Radio Button
- UI Automation, Radio Button control type
- RadioButton control type
ms.assetid: 87170464-7857-41f1-bcf7-bb41be31cb53
ms.openlocfilehash: 6d832995362041c71d92d34e529c1895848aa9cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954838"
---
# <a name="ui-automation-support-for-the-radiobutton-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle RadioButton
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle RadioButton. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Une case d’option se compose d’un bouton rond et d’un texte défini par l’application (étiquette), d’une icône ou d’une image bitmap qui indique un choix que l’utilisateur peut faire en sélectionnant le bouton. Une application utilise généralement des cases d’option dans une zone de groupe pour permettre à l’utilisateur de choisir parmi un ensemble d’options connexes mais s’excluant mutuellement. Par exemple, l’application peut présenter un groupe de cases d’option parmi lesquelles l’utilisateur peut sélectionner une préférence de format pour le texte sélectionné dans la zone cliente. L’utilisateur peut sélectionner un format aligné à gauche, aligné à droite ou centré en cochant la case d’option correspondante. En règle générale, l’utilisateur peut sélectionner une seule option à la fois parmi un ensemble de cases d’option.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requis pour le type de contrôle RadioButton. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant illustre la vue de contrôle et la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de case d’option, et décrit ce que peut contenir chaque vue. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|RadioButton|RadioButton|  
  
 Aucun enfant ne figure dans la vue de contrôle ni dans la vue de contenu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour le type de contrôle RadioButton. Pour plus d’informations [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur les propriétés, consultez [UI Automation Properties for clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les notes.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les notes.|Le nom du contrôle de case d’option est le texte qui s’affiche en regard du bouton qui maintient l’état de sélection.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les notes.|Le point interactif d’un contrôle de case d’option DOIT être un point qui définit la sélection sur la case d’option si l’utilisateur clique dessus avec le pointeur de souris.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les cases d’option sont des contrôles à étiquetage automatique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|RadioButton|Cette valeur est la même pour toutes les infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« case d’option »|Chaîne localisée correspondant au type de contrôle RadioButton.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle de case d’option est toujours inclus dans la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle de case d’option est toujours inclus dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de case d’option. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle / Propriété de modèle de contrôle|Prise en charge / Valeur|Notes|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Oui|Tous les contrôles de case d’option doivent prendre en charge le modèle Selection Item qui permet de les sélectionner.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Consultez les notes.|La propriété `SelectionContainerProperty` doit toujours être définie afin qu’un client UI Automation puisse déterminer quelles autres cases d’option dans un contexte spécifique se rapportent les unes aux autres.  Pour la version [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] de la case d’option, cette propriété n’est pas prise en charge car il n’est pas possible d’obtenir ces informations à partir de cette infrastructure héritée.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Never|La case d’option ne peut pas passer d’un état à un autre une fois qu’elle a été définie.  Ce modèle ne doit jamais être pris en charge sur la case d’option.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de case d’option. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Assistance|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.RadioButton>
- [Vue d’ensemble des types de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](../../../docs/framework/ui-automation/ui-automation-overview.md)
