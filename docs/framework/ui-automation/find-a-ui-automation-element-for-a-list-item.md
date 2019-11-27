---
title: Rechercher un élément UI Automation pour un élément de liste
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 63181de26f7d8efda99d5b5d71b006cde44823a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433545"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Rechercher un élément UI Automation pour un élément de liste
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment récupérer un <xref:System.Windows.Automation.AutomationElement> pour un élément dans une liste lorsque l’index de l’élément est connu.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux façons de récupérer un élément spécifié dans une liste, l’un à l’aide de <xref:System.Windows.Automation.TreeWalker> et l’autre à l’aide de <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 La première technique a tendance à être plus rapide pour les contrôles de [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], mais la seconde est plus rapide pour les contrôles Windows Presentation Foundation (WPF).  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Voir aussi

- [Obtaining UI Automation Elements](obtaining-ui-automation-elements.md)
