---
title: Mappage de modèle de contrôle pour les clients UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433860"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mappage de modèle de contrôle pour les clients UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique répertorie les types de contrôle et leurs modèles de contrôle associés.  
  
 Le tableau suivant organise les modèles de contrôle dans les catégories suivantes :  
  
- Prise en charge. Le contrôle doit prendre en charge ce modèle de contrôle.  
  
- Prise en charge conditionnelle. Le contrôle peut prendre en charge ce modèle de contrôle en fonction de l’état du contrôle.  
  
- Non prise en charge. Le contrôle ne prend pas en charge ce modèle de contrôle. Les contrôles personnalisés peuvent prendre en charge ce modèle de contrôle.  
  
> [!NOTE]
> Certains contrôles disposent d’une prise en charge conditionnelle pour plusieurs modèles de contrôle selon les fonctionnalités du contrôle. Par exemple, le contrôle d’élément de menu dispose d’une prise en charge conditionnelle pour le modèle de contrôle <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>ou <xref:System.Windows.Automation.SelectionItemPattern> , selon sa fonction dans le contrôle de menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Modèles de contrôle UI Automation pour les clients  
  
|Type de contrôle|Prise en charge|Prise en charge conditionnelle|Non prise en charge|  
|------------------|---------------|-------------------------|-------------------|  
|Button|aucune.|Invoke, Toggle, Expand Collapse|aucune.|  
|Calendrier|Grid, Table|Selection, Scroll|valeur|  
|Case à cocher|Basculer|aucune.|aucune.|  
|Combo Box|Développer/Réduire|Selection, Value|Scroll|  
|DataGrid|Grille|Scroll, Selection, Table|aucune.|  
|DataItem|Selection Item|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|aucune.|  
|Document|Texte|Scroll, Value|aucune.|  
|Éditer|aucune.|Text, Range Value, Value|aucune.|  
|Regrouper|aucune.|Développer/Réduire|aucune.|  
|Header|aucune.|transformation|aucune.|  
|HeaderItem|aucune.|Transform, Invoke|aucune.|  
|Lien hypertexte|Appeler|valeur|aucune.|  
|Image|aucune.|Grid Item, Table Item|Invoke, Selection Item|  
|List|aucune.|Grid, Multiple View, Scroll, Selection|Table|  
|List Item|Selection Item|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|aucune.|  
|Menu|aucune.|aucune.|aucune.|  
|Barre de menus|aucune.|Expand Collapse, Dock, Transform|aucune.|  
|Élément de menu|aucune.|Expand Collapse, Invoke, Selection Item, Toggle|aucune.|  
|Volet|aucune.|Dock. Scroll, Transform|Fenêtre|  
|ProgressBar|aucune.|Range Value, Value|aucune.|  
|RadioButton|Selection Item|aucune.|Basculer|  
|Scroll Bar|aucune.|Range Value|Scroll|  
|Séparateur|aucune.|aucune.|aucune.|  
|Curseur|aucune.|Range Value, Selection, Value|aucune.|  
|Spinner|aucune.|Range Value, Selection, Value|aucune.|  
|Bouton partagé|Invoke, Expand Collapse|aucune.|aucune.|  
|Barre d'état|aucune.|Grille|aucune.|  
|Onglet|Sélection|Scroll|aucune.|  
|TabItem|Selection Item|aucune.|Appeler|  
|Table|Grid, Grid Item, Table, Table Item|aucune.|aucune.|  
|Texte|aucune.|Grid Item, Table Item, Text|valeur|  
|Thumb|transformation|aucune.|aucune.|  
|Barre de titre|aucune.|aucune.|aucune.|  
|Tool Bar|aucune.|Dock, Expand Collapse, Transform|aucune.|  
|Tool Tip|aucune.|Text, Window|aucune.|  
|Arborescence|aucune.|Scroll, Selection|aucune.|  
|TreeItem|Développer/Réduire|Invoke, Scroll Item, Selection Item, Toggle|aucune.|  
|Fenêtre|Transform, Window|Station d' accueil|aucune.|  
  
> [!NOTE]
> Si un type de contrôle ne possède aucun modèle de contrôle pris en charge répertorié, mais possède un ou plusieurs modèles de contrôle pris en charge de manière conditionnelle, l’un de ces modèles de contrôle conditionnels est constamment pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’UI Automation](ui-automation-overview.md)
