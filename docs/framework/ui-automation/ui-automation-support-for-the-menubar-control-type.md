---
title: Prise en charge d'UI Automation pour le type de contrôle MenuBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Menu Bar control type
- control types, Menu Bar
- Menu Bar control type
ms.assetid: c1202b21-c1f0-4560-853c-7b99bd73ad97
ms.openlocfilehash: 233fdb088d31718650696d56c035cdb1a97687fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446696"
---
# <a name="ui-automation-support-for-the-menubar-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle MenuBar
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle <xref:System.Windows.Automation.ControlType.MenuBar> . Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est l’ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Ces conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Les contrôles de barre de menu constituent un exemple de contrôles qui implémentent le type de contrôle MenuBar. Les barres de menus permettent aux utilisateurs d’activer les commandes et les options contenues dans une application.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires au type de contrôle MenuBar. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles list, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de barre de menus, et décrit ce que chaque affichage peut contenir. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Vue de contenu|  
|------------------|------------------|  
|MenuBar<br /><br /> -MenuItem (1 ou plus)<br />-Autres contrôles (0 ou plusieurs)|MenuBar<br /><br /> -MenuItem (1 ou plus)<br />-Autres contrôles (0 ou plusieurs)|  
  
 Les contrôles de barre de menus peuvent contenir d’autres contrôles tels que des contrôles d’édition et des zones de liste modifiable dans leur structure. Ces contrôles supplémentaires correspondent aux « autres contrôles » répertoriés ci-dessus dans les affichages de contrôle et de contenu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour le type de contrôle de barre de menus. Pour plus d’informations sur les propriétés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Remarques|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|La valeur exposée par cette propriété doit inclure tous les contrôles qu’elle contient.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les notes.|Le contrôle de barre de menus n’a pas besoin d’un nom, sauf si une application contient plusieurs barres de menus. S’il existe plusieurs barres de menus dans une application, cette propriété doit être utilisée pour exposer des noms distinctifs, tels que « Mise en forme » ou « Mode plan ».|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Les contrôles de barre de menus n’ont jamais d’étiquette.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuBar|Cette valeur est la même pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« barre de menus »|Chaîne localisée correspondant au type de contrôle MenuBar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle de barre de menus est toujours inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle de barre de menus est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Consultez les notes.|La valeur de cette propriété varie selon que le contrôle est visible ou non à l’écran.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Selon le cas|Cette propriété indique si le contrôle de barre de menus est horizontal ou vertical.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Les contrôles de barre de menus sont actifs via le clavier, car les contrôles qu’ils contiennent peuvent recevoir le focus clavier.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consultez les notes.|Aucun scénario ne s’applique si du texte d’aide est nécessaire pour un contrôle de barre de menus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|`Null`|Les barres de menus n’ont jamais de touche accélérateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|« ALT »|La touche ALT doit toujours apporter le focus à la barre de menus de l’application.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles de barre de menus. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Assistance|Remarques|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Selon le cas|Si le contrôle peut être développé ou réduit, implémentez <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Selon le cas|Si le contrôle peut être ancré aux différentes parties de l’écran, implémentez <xref:System.Windows.Automation.Provider.IDockProvider>.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Selon le cas|Si le contrôle peut être redimensionné, pivoté ou déplacé, il doit implémenter <xref:System.Windows.Automation.Provider.ITransformProvider>.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de barre de menus. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge/Valeur|Remarques|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|Aucune|  
|Événement de modification de propriété<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>|Selon le cas|Aucune|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucune|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucune|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.ControlType.MenuBar>
- [Vue d’ensemble des types de contrôle UI Automation](ui-automation-control-types-overview.md)
- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
