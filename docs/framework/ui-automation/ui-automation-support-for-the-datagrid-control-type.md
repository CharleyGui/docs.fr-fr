---
title: Prise en charge d'UI Automation pour le type de contrôle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 1e127b4a2fdb51a151344f81e1451ecee6ca3a5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789541"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle DataGrid
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour le type de contrôle DataGrid. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété `ControlType` . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le type de contrôle DataGrid permet à un utilisateur de facilement utiliser des éléments qui contiennent des métadonnées représentées en colonnes. Les contrôles de grille de données présentent des lignes d’éléments et des colonnes d’informations sur ces éléments. Un contrôle d’affichage de liste dans Microsoft Vista Explorer est un exemple de prise en charge du type de contrôle DataGrid.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle DataGrid. Les exigences de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles de grille de données, qu’il s’agisse [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 ou Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de grille de données, et décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage de contrôle|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage du contenu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Header (0, 1 ou 2)<br /><br /> <ul><li>HeaderItem (nombre de lignes ou colonnes)</li></ul></li><li>DataItem (0 ou plus. Peut être structuré dans une hiérarchie)</li></ul>|DataGrid<br /><br /> -DataItem (0 ou plus ; peut être structuré dans la hiérarchie)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés dont la valeur ou la définition est particulièrement pertinente pour les contrôles de grille de données. Pour plus d’informations sur les propriétés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Les|Value|Remarques|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les remarques.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les remarques.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les remarques.|Pris en charge s’il existe un rectangle englobant. Si les points du rectangle englobant ne sont pas tous interactifs et que vous effectuez un test de positionnement spécialisé, vous devez remplacer et fournir un point interactif.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Cette valeur est identique pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|La valeur de cette propriété doit toujours être True. Cela signifie que le contrôle de grille de données doit toujours être inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|La valeur de cette propriété doit toujours être True. Cela signifie que le contrôle de grille de données doit toujours être inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les remarques.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consultez les remarques.|S’il existe une étiquette de texte statique, cette propriété doit exposer une référence à ce contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« grille de données »|Chaîne localisée correspondant au type de contrôle DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les remarques.|Le contrôle de grille de données obtient généralement la valeur de sa propriété `Name` à partir d’une étiquette de texte statique. En l’absence d’étiquette de texte statique, un développeur d’applications doit attribuer une valeur à la propriété `Name` . La valeur de la propriété `Name` ne doit jamais être le contenu textuel du contrôle d’édition.|  
  
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle qui doivent être pris en charge par tous les contrôles de grille de données. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Prise en charge de|Remarques|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Oui|Le contrôle de grille de données proprement dit prend toujours en charge le modèle de contrôle Grid, car les éléments qu’il contient sont des métadonnées présentées dans une grille.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Selon le cas|La possibilité de faire défiler la grille de données dépend du contenu et de la présence de barres de défilement.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Selon le cas|La possibilité de sélectionner la grille de données dépend du contenu.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Oui|Le contrôle de grille de données dispose toujours d’un en-tête dans sa sous-arborescence. Le modèle de contrôle Table doit donc être pris en charge.|  
  
 Les éléments de données dans les conteneurs de grille de données prennent en charge au minimum ce qui suit :  
  
- Modèle de contrôle Selection Item (si la grille de données est sélectionnable)  
  
- Modèle de contrôle Scroll Item (si la grille de données autorise le défilement)  
  
- Modèle de contrôle Grid Item  
  
- Modèle de contrôle Table Item  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de grille de données. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge de|Remarques|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>|Selon le cas|Si le contrôle prend en charge le modèle Scroll, il doit prendre en charge cet événement.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Obligatoire|Aucun|  
  
## <a name="date-grid-control-type-example"></a>Exemple de type de contrôle DataGrid  
 L’image suivante illustre un contrôle d’affichage de liste qui implémente le type de contrôle DataGrid.  
  
 ![Graphique d’un contrôle d’affichage de liste avec deux éléments de données](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 L’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative au contrôle d’affichage de liste sont affichés ci-dessous. Les modèles de contrôle de chaque élément Automation sont indiqués entre parenthèses.  
  
|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage de contrôle|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage du contenu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Table, Grid, Selection)</li><li>Header<br /><br /> <ul><li>HeaderItem « Nom » (Invoke)</li><li>HeaderItem « Date de modification » (Invoke)</li><li>HeaderItem « Taille » (Invoke)</li></ul></li><li>Groupe « contoso » (TableItem, GridItem, SelectionItem, table *, Grid\*)<br /><br /> <ul><li>DataItem « Accounts Receivable. doc » (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem « Accounts payable. doc » (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (Table, Grid, Selection)</li><li>Groupe « contoso » (TableItem, GridItem, SelectionItem, table *, Grid\*)<br /><br /> <ul><li>DataItem « Accounts Receivable. doc » (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem « Accounts payable. doc » (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 \* l’exemple précédent montre un DataGrid contenant plusieurs niveaux de contrôles. Le contrôle Group (« Contoso ») contient deux contrôles DataItem (« Accounts Receivable.doc » et « Accounts Payable.doc »). Une paire DataGrid/GridItem est indépendante d’une paire d’un autre niveau. Les contrôles DataItem sous un contrôle Group peuvent également être exposés en tant que type de contrôle ListItem, ce qui leur permet d’être présentés plus clairement comme des objets sélectionnables, plutôt que comme de simples éléments de données. Cet exemple n’inclut pas les sous-éléments des éléments de données groupés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
