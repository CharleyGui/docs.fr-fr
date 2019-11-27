---
title: Prise en charge d'UI Automation pour le type de contrôle List
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: c5ea011651537aa5836eeebe217239234fec40ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446733"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle List
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle List. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est l’ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Ces conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le type de contrôle List offre un moyen d’organiser un groupe plat ou des groupes d’éléments et permet à un utilisateur de sélectionner un ou plusieurs de ces éléments. Le type de contrôle List présente une petite restriction quant aux types d’éléments enfants qu’il peut contenir. Les fournisseurs UI Automation peuvent de ce fait prendre en charge un élément bien connu pour les conteneurs de sélection.  
  
 Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] décrites dans les sections suivantes s’appliquent à tous les contrôles qui implémentent le type de contrôle List, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Les contrôles de conteneur List constituent un exemple de contrôles qui implémentent le type de contrôle List.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente les deux affichages de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] concernant les contrôles list et décrit ce que chaque affichage peut contenir. L’affichage de contrôle contient uniquement des éléments qui correspondent à des contrôles, tandis que l’affichage de contenu supprime les informations redondantes de l’arborescence. Par exemple, un contrôle de texte servant d’étiquette pour une zone de liste déroulante est exposé en tant que `ComboBox NameProperty`. Comme le contrôle de texte est déjà exposé de cette manière via l’affichage de contrôle, il n’est pas nécessaire de l’exposer deux fois. De ce fait, il est supprimé de l’affichage de contenu. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|Contient les éléments qui correspondent aux contrôles.|Supprime les informations redondantes de l’arborescence pour permettre aux technologies d’assistance d’utiliser le plus petit ensemble d’informations explicites pour l’utilisateur final.|  
|Liste<br /><br /> -DataItem (0 ou plus)<br />-ListItem (0 ou plus)<br />-Group (0 ou plus)<br />-ScrollBar (0, 1 ou 2)|Liste<br /><br /> -DataItem (0 ou plus)<br />-ListItem (0 ou plus)<br />-Group (0 ou plus)|  
  
 L’affichage de contrôle pour un contrôle qui implémente le type de contrôle List (par exemple, un contrôle list) se compose des éléments suivants :  
  
- Zéro, un ou plusieurs éléments dans le contrôle de liste (les éléments peuvent être basés sur les types de contrôle d’élément de liste ou d’élément de données).
  
- Zéro ou plusieurs contrôles de groupe dans un contrôle de liste.
  
- Zéro, un ou deux contrôles de barre de défilement.
  
L’affichage de contenu pour un contrôle qui implémente le type de contrôle List (par exemple, un contrôle list) se compose des éléments suivants :  
  
- Zéro, un ou plusieurs éléments dans le contrôle de liste (les éléments peuvent être basés sur les types de contrôle d’élément de liste ou d’élément de données).
  
- Zéro ou plusieurs groupes dans le contrôle de liste.

Un contrôle list ne doit pas contenir d’éléments ayant une relation hiérarchique autre que le fait d’être regroupés. Si les éléments ont des enfants dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , le conteneur list doit être basé sur le type de contrôle Tree.  
  
 Les éléments sélectionnables dans le contrôle list sont accessibles aux descendants dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] du contrôle List. Tous les éléments du contrôle list doivent appartenir au même groupe de sélection. Les éléments sélectionnables dans la liste doivent être exposées en tant que types de contrôle ListItem (et non DataItem).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles de liste. Pour plus d’informations sur les propriétés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Remarques|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les notes.|Si le contrôle list a un point interactif (point sur lequel l’utilisateur clique pour que la liste prenne le focus), ce point doit être exposé par le biais de cette propriété.<br /><br /> Si la valeur de la propriété `IsOffScreen` a la valeur true, le <xref:System.Windows.Automation.NoClickablePointException> est déclenché.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les notes.|La valeur de la propriété Name du contrôle list doit communiquer la catégorie d’options dans laquelle l’utilisateur est invité à faire une sélection. Cette propriété tire généralement son nom d’une étiquette de texte statique. En l’absence d’étiquette de texte statique, un développeur d’applications doit exposer une valeur pour la propriété Name.<br /><br /> Le seul cas où cette propriété n’est pas obligatoire pour les contrôles list, c’est lorsque le contrôle est utilisé dans la sous-arborescence d’un autre contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consultez les notes.|S’il existe une étiquette de texte statique, cette propriété doit exposer une référence à ce contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Liste|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« liste »|Chaîne localisée correspondant au type de contrôle List.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle de liste est toujours inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle de liste est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Si le conteneur peut accepter l’entrée au clavier, cette propriété doit avoir la valeur true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consultez les notes.|Le texte d’aide sur les contrôles list doit expliquer la raison pour laquelle l’utilisateur est invité à faire un sélection dans une liste d’options. Par exemple, « la sélection d’un élément dans cette liste a pour effet de définir la résolution d’affichage de votre moniteur ».|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Modèles de contrôle et propriétés UI Automation requis  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles de liste. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle/Propriété de modèle|Prise en charge/Valeur|Remarques|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Obligatoire|Tous les contrôles qui prennent en charge le type de contrôle List doivent implémenter `ISelectionProvider` quand un état de sélection est maintenu entre les éléments contenus dans le contrôle. Si les éléments présents dans le conteneur ne peuvent pas être sélectionnés, le type de contrôle Group doit être utilisé.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Selon le cas|Avec les contrôles List, la sélection d’un élément n’est pas toujours obligatoire.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Selon le cas|Les contrôles List peuvent être des conteneurs à sélection unique ou multiple.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Selon le cas|Implémentez ce modèle de contrôle si les éléments du conteneur peuvent faire l’objet d’un défilement.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Selon le cas|Implémentez ce modèle quand la navigation dans la grille doit être disponible sur un élément, par élément.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contrôle peut prendre en charge plusieurs affichages des éléments du conteneur.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Jamais|`ITableProvider` n’est jamais pris en charge pour le type de contrôle List. Si le contrôle doit prendre en charge ce modèle de contrôle, le contrôle doit être basé sur le type de contrôle Data Grid.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles list. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge/Valeur|Remarques|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Selon le cas|Aucune|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>|Selon le cas|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>|Selon le cas|Aucune|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucune|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucune|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.List>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
