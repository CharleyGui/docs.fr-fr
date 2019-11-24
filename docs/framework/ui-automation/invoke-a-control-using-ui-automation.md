---
title: Appeler un contrôle à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447002"
---
# <a name="invoke-a-control-using-ui-automation"></a>Appeler un contrôle à l'aide d'UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment effectuer les tâches suivantes :  
  
- Rechercher un contrôle qui correspond aux conditions de la propriété spécifique en parcourant la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour l’application cible.  
  
- Créer un <xref:System.Windows.Automation.AutomationElement> pour chaque contrôle.  
  
- Obtenir un objet <xref:System.Windows.Automation.InvokePattern> depuis n’importe quel élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] trouvé qui prend en charge le modèle de contrôle <xref:System.Windows.Automation.InvokePattern> .  
  
- Utiliser <xref:System.Windows.Automation.InvokePattern.Invoke%2A> pour appeler le contrôle à partir d’un gestionnaire d’événements client.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> de la classe <xref:System.Windows.Automation.AutomationElement> pour générer un objet <xref:System.Windows.Automation.InvokePattern> et appeler un contrôle à l’aide de la méthode <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Voir aussi

- [InvokePattern, ExpandCollapsePattern, and TogglePattern Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
