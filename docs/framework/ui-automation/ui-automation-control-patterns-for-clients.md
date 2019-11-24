---
title: Modèles de contrôle UI Automation pour les clients
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 193049aed6da3375b687e465678dca4dc90e6b39
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448815"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Modèles de contrôle UI Automation pour les clients
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette vue d’ensemble présente des modèles de contrôle pour les clients UI Automation. Elle inclut des informations sur la façon dont un client UI Automation peut utiliser des modèles de contrôle pour accéder aux informations sur l’[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Les modèles de contrôle permettent de catégoriser et d'exposer les fonctionnalités d'un contrôle, indépendamment du type de contrôle ou de l'apparence du contrôle. Les clients UI Automation peuvent examiner un <xref:System.Windows.Automation.AutomationElement> pour déterminer les modèles de contrôle pris en charge et s’assurer du comportement du contrôle.  
  
 For a complete list of control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtention de modèles de contrôle  
 Les clients récupèrent un modèle de contrôle d'un <xref:System.Windows.Automation.AutomationElement> en appelant <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Les clients peuvent utiliser la méthode <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> ou une propriété `IsPatternAvailable` individuelle (par exemple, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) pour déterminer si un modèle ou un groupe de modèles est pris en charge sur <xref:System.Windows.Automation.AutomationElement>. Toutefois, il est plus efficace d'essayer d'obtenir le modèle de contrôle et de tester une référence `null` que de vérifier les propriétés prises en charge et de récupérer le modèle de contrôle, car cela entraîne moins d'appels interprocessus.  
  
 L'exemple suivant montre comment obtenir un modèle de contrôle <xref:System.Windows.Automation.TextPattern> d'un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Récupération de propriétés sur des modèles de contrôle  
 Les clients peuvent récupérer les valeurs de propriété sur les modèles de contrôle en appelant <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> et en effectuant le cast de l'objet retourné en un type approprié. For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
 In addition to the `GetPropertyValue` methods, property values can be retrieved through the common language runtime (CLR) accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Contrôles avec modèles variables  
 Certains types de contrôles prennent en charge différents modèles selon leur état ou la manière dont le contrôle est utilisé. Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), Microsoft Excel Charts (Pie, Line, Bar, Cell Value with a formula), Microsoft Word's document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and Microsoft Windows Media Player skins.  
  
 Les contrôles implémentant des types de contrôles personnalisés peuvent disposer de n’importe quel jeu de modèles de contrôle nécessaires pour représenter leurs fonctionnalités.  
  
## <a name="see-also"></a>Voir aussi

- [Modèles de contrôle UI Automation](ui-automation-control-patterns.md)
- [Modèle de texte UI Automation](ui-automation-text-pattern.md)
- [Appeler un contrôle à l’aide d’UI Automation](invoke-a-control-using-ui-automation.md)
- [Obtenir l’état bascule d’une case à cocher à l’aide d’UI Automation](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mappage de modèle de contrôle pour les clients UI Automation](control-pattern-mapping-for-ui-automation-clients.md)
- [TextPattern Insert Text Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextPattern Search and Selection Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvokePattern, ExpandCollapsePattern, and TogglePattern Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
