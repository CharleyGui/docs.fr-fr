---
title: Prise en charge d'UI Automation pour le type de contrôle Edit
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 500dc450ad171ed50316c8e08d62258d745049cb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448459"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Edit

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).

Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle Edit. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.

Les contrôles Edit permettent à un utilisateur d’afficher et modifier une simple ligne de texte sans une prise en charge évoluée de la mise en forme.

Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requis pour le type de contrôle Edit. Les exigences [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles d’édition, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation requise

Le tableau suivant illustre la vue de contrôle et la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’édition, et décrit ce que peut contenir chaque vue. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).

|Affichage de contrôle|Vue de contenu|
|------------------|------------------|
|Éditer|Éditer|

Les contrôles qui implémentent le type de contrôle Edit n’auront jamais de barre de défilement dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] car il s’agit d’un contrôle à ligne unique. Dans certains scénarios de disposition, la ligne de texte unique peut faire l’objet d’un retour automatique à la ligne. Le type de contrôle Edit est parfaitement adapté pour la maintenance de petites quantités de texte modifiable ou sélectionnable.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises

Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles d’édition. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).

|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|valeur|Notes|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Voir les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Voir les notes.|Rectangle externe qui contient l’ensemble du contrôle.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Voir les notes.|Le contrôle d’édition doit avoir un point interactif qui donne le focus d’entrée à la partie d’édition du contrôle quand un utilisateur clique dessus avec la souris.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Voir les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Voir les notes.|Le nom du contrôle d’édition est habituellement généré à partir d’une étiquette de texte statique. En l’absence d’une telle étiquette, le développeur de l’application doit assigner une valeur de propriété pour `Name` . La propriété `Name` ne doit jamais contenir le contenu textuel du contrôle d’édition.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Voir les notes.|Si une étiquette de texte statique est associée au contrôle, cette propriété doit exposer une référence à ce contrôle. Si le contrôle de texte est un sous-composant d’un autre contrôle, aucune propriété `LabeledBy` n’est définie.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Éditer|Cette valeur est la même pour toutes les infrastructures d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« édition »|Chaîne localisée correspondant au type de contrôle Edit.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle d’édition est toujours inclus dans la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle d’édition est toujours inclus dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Voir les notes.|Cette propriété doit avoir la valeur true pour les contrôles d’édition qui contiennent des mots de passe. Si un contrôle d’édition contient du contenu de mot de passe, cette propriété peut être utilisée par un lecteur d’écran pour déterminer si les séquences de touches doivent être lues au moment où l’utilisateur les tape.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Modèles de contrôle et propriétés UI Automation obligatoires

Le tableau suivant répertorie les modèles de contrôle qui doivent être pris en charge par tous les contrôles d’édition. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).

|Modèle de contrôle / Propriété de modèle de contrôle|Prise en charge / Valeur|Notes|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Selon le cas|Les contrôles d’édition doivent prendre en charge le modèle de contrôle Text parce que les informations de texte détaillées doivent toujours être disponibles pour les clients.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Selon le cas|Tous les contrôles d’édition qui utilisent une chaîne doivent exposer le modèle Value.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Voir les notes.|Cette propriété doit être définie pour indiquer si le contrôle peut avoir une valeur définie par programmation ou peut être modifiée par l’utilisateur.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Voir les notes.|Cette propriété retourne le contenu textuel du contrôle d’édition. Si la propriété `IsPasswordProperty` a la valeur `true`, elle doit déclencher une exception `InvalidOperationException` quand elle est demandée.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Selon le cas|Tous les contrôles d’édition qui utilisent une plage numérique doivent exposer le modèle de contrôle Range Value.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Voir les notes.|Cette propriété doit représenter la plus petite valeur pouvant être affectée au contenu du contrôle d’édition.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Voir les notes.|Cette propriété doit représenter la plus grande valeur pouvant être affectée au contenu du contrôle d’édition.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Voir les notes.|Cette propriété doit indiquer le nombre de décimales pouvant être défini pour la valeur. Si la modification accepte uniquement des entiers, `SmallChangeProperty` doit avoir la valeur 1. Si la modification accepte une plage entre 1.0 et 2.0, `SmallChangeProperty` doit avoir la valeur 0.1. Si le contrôle d’édition accepte une plage entre 1.00 et 2.00, `SmallChangeProperty` doit avoir la valeur 0.001.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Cette propriété n’est pas tenue d’être exposée sur un contrôle d’édition.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Voir les notes.|Cette propriété indique le contenu numérique du contrôle d’édition. Quand une valeur plus précise est définie par un client [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dans les plages spécifiées dans les propriétés `Minimum` et `Maximum` , la propriété Value est automatiquement arrondie à la valeur acceptée la plus proche.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Événements UI Automation requis

Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’édition. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).

|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Assistance|Notes|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Obligatoire|aucune.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Obligatoire|aucune.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Obligatoire|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> .|Obligatoire|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> .|Selon le cas|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> .|Never|aucune.|
|Événement de modification de propriété<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> .|Selon le cas|Si le contrôle prend en charge le modèle de contrôle Range Value, il doit prendre en charge cet événement.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|aucune.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|aucune.|

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Edit>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
