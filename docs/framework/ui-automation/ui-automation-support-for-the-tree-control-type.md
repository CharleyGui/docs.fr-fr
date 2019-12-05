---
title: Prise en charge d'UI Automation pour le type de contrôle Tree
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree
- Tree control type
- UI Automation, Tree control type
ms.assetid: 312dd04d-a86b-4072-8b12-2beeabdff5e3
ms.openlocfilehash: 412bcde811c0c2157088763e59c0d1e0fab2adbe
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800228"
---
# <a name="ui-automation-support-for-the-tree-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Tree
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle Tree. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le type de contrôle Tree est utilisé pour les conteneurs dont le contenu est pertinent en tant que hiérarchie de nœuds, comme c’est le cas pour l’affichage des fichiers et des dossiers dans le volet gauche de l’Explorateur Microsoft Windows. Chaque nœud peut contenir d’autres nœuds, appelés nœuds enfants. Vous pouvez afficher les nœuds parents, ou nœuds qui contiennent des nœuds enfants, sous forme développée ou réduite.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle Tree. Les exigences [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles d’arborescence, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation requise  
 Le tableau suivant représente l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’arborescence. En outre, il décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|Arborescence<br /><br /> <ul><li>DataItem (0 ou plus)</li><li>TreeItem (0 ou plus)<br /><br /> <ul><li>TreeItem (0 ou plus)•    …</li></ul></li><li>ScrollBar (0, 1, 2)</li></ul>|Arborescence<br /><br /> <ul><li>DataItem (0 ou plus)</li><li>TreeItem (0 ou plus)<br /><br /> <ul><li>TreeItem (0 ou plus)•    …</li></ul></li></ul>|  
  
 L’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] comprend :  
  
- zéro ou plusieurs éléments dans le conteneur (les éléments peuvent être basés sur les types de contrôle TreeItem, DataItem ou autres) ;  
  
- zéro, une ou deux barres de défilement.  
  
 L’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] comprend zéro ou plusieurs éléments dans le conteneur (les éléments peuvent être basés sur les types de contrôle TreeItem, DataItem ou autres).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles de liste. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Voir les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Voir les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Voir les notes.|Les contrôles d’arborescence ont un point interactif qui déclenche l’obtention du focus par l’arborescence ou l’un des éléments du conteneur d’arborescence. Vous obtenez un point interactif pour une arborescence uniquement si vous pouvez cliquer à un emplacement qui n’entraîne pas la sélection ou l’obtention du focus par l’un des éléments.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Arborescence|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle d’arborescence est toujours inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle d’arborescence est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Voir les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Voir les notes.|Si une étiquette est associée au contrôle d’arborescence, cette propriété retourne <xref:System.Windows.Automation.AutomationElement> pour cette étiquette. Sinon, la propriété retourne une référence null (`Nothing` dans Microsoft Visual Basic .NET).|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"arborescence"|Chaîne localisée correspondant au type de contrôle List.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Voir les notes.|La valeur de propriété du nom d’un contrôle d’arborescence provient généralement du texte correspondant à l’étiquette du contrôle. En l’absence d’étiquette de texte, le développeur d’applications doit fournir une valeur pour cette propriété.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation requis  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles list. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle/Propriété de modèle|Prise en charge / Valeur|Notes|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Selon le cas|Les contrôles d’arborescence qui contiennent un ensemble d’éléments sélectionnables doivent implémenter ce modèle de contrôle. Ce modèle de contrôle n’a pas à être implémenté si la sélection d’un élément ne vise pas à transmettre des informations importantes à l’utilisateur.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Voir les notes.|Implémentez cette propriété si le contrôle d’arborescence prend en charge la sélection multiple (la plupart des contrôles d’arborescence ne prennent pas en charge la sélection multiple).|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Voir les notes.|La valeur de cette propriété est exposée si le contrôle nécessite la sélection d’un élément.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contenu du conteneur d’arborescence peut faire l’objet d’un défilement.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’arborescence. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge de|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> .|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Tree>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
