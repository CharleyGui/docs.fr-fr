---
title: Rechercher un élément UI Automation basé sur une condition de propriété
description: Rechercher un élément UI Automation basé sur une condition de propriété. Localisez un élément dans l’arborescence UI Automation en fonction d’une propriété ou de propriétés spécifiques.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 5e5fa4fde9049bd87b2722fa9b7d084d96ff6f42
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168431"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Rechercher un élément UI Automation basé sur une condition de propriété
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment rechercher un élément dans l' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arborescence en fonction d’une propriété ou de propriétés spécifiques.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un ensemble de conditions de propriété est spécifié, qui identifient un certain (e) élément (ou) d’intérêt dans l' <xref:System.Windows.Automation.AutomationElement> arborescence. Une recherche de tous les éléments correspondants est ensuite effectuée avec la <xref:System.Windows.Automation.AutomationElement.FindAll%2A> méthode qui incorpore une série d' <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.  
  
> [!NOTE]
> Lors de la recherche à partir du <xref:System.Windows.Automation.AutomationElement.RootElement%2A> , vous devez essayer d’obtenir uniquement les enfants directs. Une recherche de descendants peut itérer au sein de centaines, voire de milliers d’éléments, ce qui peut entraîner un dépassement de capacité de la pile. Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple d’élément de menu InvokePattern et ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Obtention d'éléments UI Automation](obtaining-ui-automation-elements.md)
- [Utiliser la propriété AutomationID](use-the-automationid-property.md)
