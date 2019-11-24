---
title: Prise en charge d'UI Automation pour le type de contrôle DataItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: 9097fdcffb236d08264b881a171a86dcf8801133
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447940"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle DataItem
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour le type de contrôle DataItem. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Ces conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Une entrée dans une liste de contacts est un exemple de contrôle d’élément de données. Un contrôle d’élément de données contient des informations intéressantes pour l’utilisateur final. Il est plus complexe que l’élément de liste simple, car il contient des informations plus détaillées.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires pour le type de contrôle DataItem. Les exigences relatives à [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles d’élément de données, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation requise  
 Le tableau suivant représente l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’élément de données. En outre, il décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – Vue de contrôle|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage du contenu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -   Varies (0 or more; can be structured in hierarchy)|DataItem<br /><br /> -   Varies (0 or more; can be structured in hierarchy)|  
  
 Un élément de données dans une grille de données peut héberger divers objets, notamment une autre couche d’éléments de données ou des éléments de grille spécifiques tels que du texte, des images ou des contrôles d’édition. Si l’élément de données a un rôle d’objet spécifique, il doit être exposé en tant que type de contrôle spécifique, par exemple un type de contrôle ListItem pour un élément de données sélectionnable dans la grille.  
  
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés dont la valeur ou la définition est particulièrement pertinente pour les contrôles d’élément de données. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|Property|valeur|Notes|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Voir les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Voir les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Voir les notes.|Pris en charge s’il existe un rectangle englobant. Si les points du rectangle englobant ne sont pas tous interactifs et que vous effectuez un test de positionnement spécialisé, vous devez remplacer et fournir un point interactif.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle d’élément de données doit toujours être du contenu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle d’élément de données doit toujours être un contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Voir les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Voir les notes.|Si le contrôle contient l’état mis à jour dynamiquement, cette propriété doit être prise en charge pour qu’une technologie d’assistance puisse recevoir des mises à jour quand l’état de l’élément change.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Voir les notes.|Il s’agit de la valeur de chaîne qui transmet à l’utilisateur final l’objet sous-jacent représenté par l’élément. « Fichier multimédia » ou « Contact » en sont des exemples.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les contrôles d’élément de données n’ont pas d’étiquette de texte statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"élément de données"|Chaîne localisée correspondant au type de contrôle DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Voir les notes.|Le contrôle d’élément de données contient toujours un élément de texte principal qui se rapporte à ce que l’utilisateur peut associer comme identificateur le plus sémantique pour l’élément.|  
  
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation requis  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’élément de données. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Assistance|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Selon le cas|Si l’élément de données peut être développé ou réduit pour afficher et masquer des informations, le modèle ExpandCollapse doit être pris en charge.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Selon le cas|Les éléments de données prennent en charge le modèle GridItem quand une collection d’éléments de données est disponible dans un conteneur pouvant être parcouru de manière spatiale d’un élément à un autre.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Selon le cas|Tous les éléments de données prennent en charge la capacité de défilement de l’affichage via le modèle ScrollItem quand leur conteneur de données contient plus d’éléments que l’écran ne peut en afficher.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Oui|Tous les éléments de données doivent prendre en charge le modèle SelectionItem pour indiquer le moment où l’élément est sélectionné.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Selon le cas|Si l’élément de données est contenu dans un contrôle de type DataGrid, il prend en charge ce modèle.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Selon le cas|Si l’élément de données contient un état qui peut être parcouru.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Selon le cas|Si le texte principal de l’élément de données est modifiable, le modèle Value doit être pris en charge.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Utilisation d’éléments de données dans les longues listes  
 Les longues listes sont souvent des données virtualisées dans des infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pour faciliter les performances. Ainsi, un client UI Automation ne peut pas utiliser la fonctionnalité de requête [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour capturer le contenu de l’arborescence complète de la même façon que dans d’autres conteneurs d’éléments. Un client doit faire défiler l’élément dans l’affichage (ou développer le contrôle pour afficher toutes les options pertinentes) avant d’accéder à l’ensemble des informations de l’élément de données.  
  
 When calling `SetFocus` on the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element for the data item, the Microsoft Windows Explorer case will return successfully and cause focus to be set to the Edit within the data item subtree.  
  
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’élément de données. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Assistance|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> .|Obligatoire|aucune.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|aucune.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Selon le cas|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> .|Selon le cas|aucune.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Obligatoire|aucune.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obligatoire|aucune.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obligatoire|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> .|Selon le cas|aucune.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> .|Selon le cas|aucune.|  
  
## <a name="dataitem-control-type-example"></a>Exemple de type de contrôle DataItem  
 L’image suivante illustre un contrôle de type DataItem dans un contrôle ListView avec prise en charge des informations détaillées pour les colonnes.  
  
 ![Graphic of a List View control with two data items](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 L’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative au contrôle d’élément de données sont indiqués ci-dessous. Les modèles de contrôle de chaque élément Automation sont indiqués entre parenthèses. Le groupe « Contoso » fait également partie de la grille du contrôle hôte de grille de données.  
  
|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – Vue de contrôle|Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Affichage du contenu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-   Group "Contoso" (Table, Grid)<br />-   DataItem "Accounts Receivable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   Image "Accounts Receivable.doc"<br />-   Edit "Name" (TableItem, GridItem, Value "Accounts Receivable.doc")<br />-   Edit "Date modified" (TableItem, GridItem, Value "8/25/2006 3:29 PM")<br />-   Edit "Size" (GridItem, TableItem, Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-   Group "Contoso" (Table, Grid)<br />-   DataItem "Accounts Receivable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   Image "Accounts Receivable.doc"<br />-   Edit "Name" (TableItem, GridItem, Value "Accounts Receivable.doc")<br />-   Edit "Date modified" (TableItem, GridItem, Value "8/25/2006 3:29 PM")<br />-   Edit "Size" (GridItem, TableItem, Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 Si une grille représente une liste d’éléments sélectionnables, les éléments d’interface correspondants peuvent être exposés avec le type de contrôle ListItem au lieu du type de contrôle DataItem. Dans l’exemple précédent, vous pouvez améliorer les éléments DataItem ("Accounts Receivable.doc" et "Accounts Payable.doc") sous Group ("Contoso") en les exposant en tant que types de contrôle ListItem, car ce type prend déjà en charge le modèle de contrôle SelectionItem.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.DataItem>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
