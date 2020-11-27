---
title: Rechercher un élément UI Automation pour un élément de liste
description: Consultez un exemple qui montre comment rechercher un élément UI Automation pour un élément de liste lorsque l’index de l’élément est connu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276475"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Rechercher un élément UI Automation pour un élément de liste

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment récupérer un <xref:System.Windows.Automation.AutomationElement> pour un élément dans une liste lorsque l’index de l’élément est connu.  
  
## <a name="example"></a> Exemple  

 L’exemple suivant montre deux façons de récupérer un élément spécifié dans une liste, l’une utilisant <xref:System.Windows.Automation.TreeWalker> et l’autre à l’aide de <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .  
  
 La première technique a tendance à être plus rapide pour les contrôles Win32, mais la seconde est plus rapide pour les contrôles Windows Presentation Foundation (WPF).  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Voir aussi

- [Obtention d'éléments UI Automation](obtaining-ui-automation-elements.md)
