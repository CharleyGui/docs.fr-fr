---
title: Obtenir des modèles de contrôle UI Automation pris en charge
description: Lisez un exemple qui montre comment récupérer des objets de modèle de contrôle pris en charge à partir d’éléments UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 68abe272e91c40932aba5bcf99394c4a8f815c53
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276449"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Obtenir des modèles de contrôle UI Automation pris en charge

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir d’éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="obtain-all-control-patterns"></a>Obtenir tous les modèles de contrôle  
  
1. Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle de l’élément.  
  
> [!CAUTION]
> Il est fortement déconseillé d’utiliser <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> sur un client. Cela peut dégrader sérieusement les performances, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant. Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles les plus intéressants.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obtenir un modèle de contrôle spécifique  
  
1. Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour rechercher un modèle spécifique. Ces méthodes sont similaires, mais si le modèle est introuvable, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retourne la valeur `false`.  
  
## <a name="example"></a> Exemple  

 L’exemple suivant récupère un élément <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un modèle <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
