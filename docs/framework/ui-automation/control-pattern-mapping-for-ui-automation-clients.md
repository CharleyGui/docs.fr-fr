---
title: Mappage de modèle de contrôle pour les clients UI Automation
description: Affichez une table de mappage de modèle de contrôle pour les clients UI Automation. Les actions pour certains types de contrôle peuvent être prises en charge, prises en charge de manière conditionnelle ou non prises en charge.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: aaab4639a7573dd090af2e6d9bb06f896c4728f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276553"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mappage de modèle de contrôle pour les clients UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique répertorie les types de contrôle et leurs modèles de contrôle associés.  
  
 Le tableau suivant organise les modèles de contrôle dans les catégories suivantes :  
  
- Pris en charge. Le contrôle doit prendre en charge ce modèle de contrôle.  
  
- Prise en charge conditionnelle. Le contrôle peut prendre en charge ce modèle de contrôle en fonction de l’état du contrôle.  
  
- Non pris en charge. Le contrôle ne prend pas en charge ce modèle de contrôle. Les contrôles personnalisés peuvent prendre en charge ce modèle de contrôle.  
  
> [!NOTE]
> Certains contrôles disposent d’une prise en charge conditionnelle pour plusieurs modèles de contrôle selon les fonctionnalités du contrôle. Par exemple, le contrôle d’élément de menu dispose d’une prise en charge conditionnelle pour le modèle de contrôle <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>ou <xref:System.Windows.Automation.SelectionItemPattern> , selon sa fonction dans le contrôle de menu.  
  
<a name="control_mapping_clients"></a>

## <a name="ui-automation-control-patterns-for-clients"></a>Modèles de contrôle UI Automation pour les clients  
  
|Type de contrôle|Prise en charge|Prise en charge conditionnelle|Non pris en charge|  
|------------------|---------------|-------------------------|-------------------|  
|Bouton|None|Invoke, Toggle, Expand Collapse|None|  
|Calendrier|Grid, Table|Selection, Scroll|Valeur|  
|Case à cocher|Bascule|None|None|  
|Combo Box|Développer/Réduire|Selection, Value|Scroll|  
|Grille de données|Grille|Scroll, Selection, Table|None|  
|DataItem|Selection Item|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|None|  
|Document|Texte|Scroll, Value|None|  
|Modifier|None|Text, Range Value, Value|None|  
|Groupe|None|Développer/Réduire|None|  
|En-tête|None|Transformer|None|  
|HeaderItem|None|Transform, Invoke|None|  
|Hyperlink|Appeler|Valeur|None|  
|Image|None|Grid Item, Table Item|Invoke, Selection Item|  
|List|None|Grid, Multiple View, Scroll, Selection|Table de charge de travail|  
|List Item|Selection Item|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|None|  
|Menu|None|None|None|  
|Barre de menus|None|Expand Collapse, Dock, Transform|None|  
|Élément de menu|None|Expand Collapse, Invoke, Selection Item, Toggle|None|  
|Volet|None|Dock. Scroll, Transform|Fenêtre|  
|ProgressBar|None|Range Value, Value|None|  
|RadioButton|Selection Item|None|Bascule|  
|Scroll Bar|None|Range Value|Scroll|  
|Séparateur|None|None|None|  
|Curseur|None|Range Value, Selection, Value|None|  
|Spinner|None|Range Value, Selection, Value|None|  
|Bouton partagé|Invoke, Expand Collapse|None|None|  
|Barre d’état|None|Grille|None|  
|Onglet|Sélection|Scroll|None|  
|TabItem|Selection Item|None|Appeler|  
|Table de charge de travail|Grid, Grid Item, Table, Table Item|None|None|  
|Texte|None|Grid Item, Table Item, Text|Valeur|  
|Thumb|Transformer|None|None|  
|Barre de titre|None|None|None|  
|Tool Bar|None|Dock, Expand Collapse, Transform|None|  
|Tool Tip|None|Text, Window|None|  
|Arborescence|None|Scroll, Selection|None|  
|TreeItem|Développer/Réduire|Invoke, Scroll Item, Selection Item, Toggle|None|  
|Fenêtre|Transform, Window|Ancrer|None|  
  
> [!NOTE]
> Si un type de contrôle ne possède aucun modèle de contrôle pris en charge répertorié, mais possède un ou plusieurs modèles de contrôle pris en charge de manière conditionnelle, l’un de ces modèles de contrôle conditionnels est constamment pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
