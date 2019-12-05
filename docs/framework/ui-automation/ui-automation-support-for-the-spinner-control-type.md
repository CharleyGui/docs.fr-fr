---
title: Prise en charge d'UI Automation pour le type de contrôle Spinner
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: 6bd080a2e95952bc2d11bd3c3bc9eaa28e72684a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801799"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle Spinner
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle Spinner. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Ces conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Les contrôles compteur sont utilisés pour effectuer une sélection parmi un domaine d’éléments ou une plage de nombres.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle Spinner. Les exigences [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles compteur, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation requise  
 Le tableau suivant représente l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles compteur quand ils prennent en charge les modèles de contrôle RangeValue, Value et Selection. En outre, il décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
 **Modèle de contrôle RangeValue ou Value**  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|Spinner<br /><br /> -Edit (0 ou 1)<br />-Button (2)|Spinner|  
  
 **Selection (modèle de contrôle)**  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|Spinner<br /><br /> -Edit (0 ou 1)<br />-Button (2)<br />-Item List (0 ou plus)|Spinner<br /><br /> -ListItem (0 ou plus)|  
  
 Pour vous assurer que les deux boutons de la sous-arborescence de la vue de contrôle peuvent être distingués par des outils de test automatisés, affectez le `SmallIncrement` ou `SmallDecrement` `AutomationId` selon le cas. Pour certaines implémentations, le contrôle d’édition associé peut être un homologue du contrôle compteur.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles compteur. Pour plus d’informations sur les propriétés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Voir les notes.|La valeur de cette propriété doit être unique pour tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Voir les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Voir les notes.|Le point interactif du contrôle compteur donne le focus à la partie d’édition du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Voir les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Voir les notes.|Le contrôle compteur tire généralement son nom d’une étiquette de texte statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Voir les notes.|Les contrôles compteur ont une étiquette de texte statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Spinner|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"compteur"|Chaîne localisée correspondant au type de contrôle Spinner.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle compteur doit toujours être du contenu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle compteur doit toujours être un contrôle.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Modèles de contrôle et propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles compteur. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle/Propriété de modèle|Prise en charge / Valeur|Notes|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Selon le cas|Les contrôles compteur qui comportent une liste d’éléments à sélectionner doivent prendre en charge ce modèle.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Les contrôles compteur sont toujours des conteneurs à sélection unique.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Selon le cas|Les contrôles compteur qui couvrent une plage numérique peuvent prendre en charge ce modèle.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Selon le cas|Les contrôles compteur qui couvrent un ensemble discret d’options ou de nombres peuvent prendre en charge ce modèle.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles compteur. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge de|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> .|Selon le cas|Aucun|  
|Événement de modification de propriété<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> .|Selon le cas|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.Spinner>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
