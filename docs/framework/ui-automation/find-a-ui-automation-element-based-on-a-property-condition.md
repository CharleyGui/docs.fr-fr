---
title: Rechercher un élément UI Automation basé sur une condition de propriété
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 536a71532f02782f9e84bb2bd086af212a77c0da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043664"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Rechercher un élément UI Automation basé sur une condition de propriété
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment rechercher un élément dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] l’arborescence en fonction d’une propriété ou de propriétés spécifiques.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un ensemble de conditions de propriété est spécifié, qui identifient un certain (e) élément (ou <xref:System.Windows.Automation.AutomationElement> ) d’intérêt dans l’arborescence. Une recherche de tous les éléments correspondants est ensuite effectuée avec <xref:System.Windows.Automation.AutomationElement.FindAll%2A> la méthode qui incorpore une série d' <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.  
  
> [!NOTE]
> Lors de la recherche <xref:System.Windows.Automation.AutomationElement.RootElement%2A>à partir du, vous devez essayer d’obtenir uniquement les enfants directs. Une recherche de descendants peut itérer au sein de centaines, voire de milliers d’éléments, ce qui peut entraîner un dépassement de capacité de la pile. Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple d’élément de menu InvokePattern et ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Obtention d’éléments UI Automation](obtaining-ui-automation-elements.md)
- [Utiliser la propriété AutomationID](use-the-automationid-property.md)
