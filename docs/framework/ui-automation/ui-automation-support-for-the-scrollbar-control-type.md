---
title: Prise en charge d'UI Automation pour le type de contrôle ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
ms.openlocfilehash: f983bd080d20a82d814445bfd90d145039d96b77
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041195"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle ScrollBar
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle ScrollBar. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Les contrôles de barre de défilement permettent à un utilisateur de faire défiler le contenu d’une fenêtre ou d’un conteneur d’élément. Le contrôle est constitué d’un ensemble de boutons et d’un contrôle curseur de position.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle ScrollBar. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de barre de défilement. En outre, il décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|ScrollBar<br /><br /> -Button (2 ou 4)<br />-Thumb (0 i :<0)|Non applicable. Le contrôle de barre de défilement n’a pas de contenu.|  
  
 Le contrôle de barre de défilement a toujours entre trois et cinq enfants. Dans la mesure où la sous-arborescence a plusieurs contrôles bouton, vous devez définir une valeur <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> spécifique pour chaque élément afin de les rendre détectables pour les outils d’automatisation des tests.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement adaptée aux contrôles de barre de défilement. Notez qu’un contrôle de barre de défilement n’a jamais de contenu. Ses fonctionnalités sont exposées via le modèle de contrôle Scroll, qui est pris en charge sur le conteneur faisant l’objet d’un défilement.  
  
 Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les notes.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|Le contrôle de barre de défilement n’a pas d’éléments de contenu. Par ailleurs, la définition de `NameProperty` n’est pas obligatoire.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Non numérique.|Le contrôle de barre de défilement n’a pas de points interactifs.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les barres de défilement n’ont pas d’étiquettes.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Cette valeur est la même pour toutes les infrastructures. Les barres de défilement qui fonctionnent en tant que curseurs doivent utiliser le type de contrôle Slider.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"barre de défilement"|Chaîne localisée correspondant au type de contrôle Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Le contrôle de barre de défilement n’est jamais un élément de contenu. Si la barre de défilement est un contrôle autonome, ce dernier doit respecter le type de contrôle Slider, et retourner `ControlType.Slider` pour la propriété `ControlType` .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|La barre de défilement doit toujours être un contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|True|Le contrôle de barre de défilement doit toujours exposer son orientation horizontale ou verticale.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles de barre de défilement. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md). Notez que si une barre de défilement est utilisée comme contrôle uniquement pour la manipulation de la souris, elle ne prend pas en charge les modèles de contrôle. Si elle est utilisée comme contrôle de curseur dans une application, le type de contrôle Slider doit lui être attribué.  
  
|Modèle de contrôle|Assistance|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Never|Le modèle de contrôle Scroll n’est jamais directement pris en charge sur la barre de défilement.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Selon le cas|Cette fonctionnalité doit être prise en charge uniquement si le modèle de contrôle Scroll n’est pas pris en charge sur le conteneur comportant la barre de défilement.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de barre de défilement. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge/valeur|Notes|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>|Never|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.ScrollBar>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
