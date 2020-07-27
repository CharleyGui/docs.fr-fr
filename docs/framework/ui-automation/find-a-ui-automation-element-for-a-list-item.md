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
ms.openlocfilehash: ec6464bc0ec504fd34ed113c9bed1a54a7d4eaec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168412"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="cef28-103">Rechercher un élément UI Automation pour un élément de liste</span><span class="sxs-lookup"><span data-stu-id="cef28-103">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="cef28-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cef28-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cef28-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cef28-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cef28-106">Cette rubrique montre comment récupérer un <xref:System.Windows.Automation.AutomationElement> pour un élément dans une liste lorsque l’index de l’élément est connu.</span><span class="sxs-lookup"><span data-stu-id="cef28-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cef28-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="cef28-107">Example</span></span>  
 <span data-ttu-id="cef28-108">L’exemple suivant montre deux façons de récupérer un élément spécifié dans une liste, l’une utilisant <xref:System.Windows.Automation.TreeWalker> et l’autre à l’aide de <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="cef28-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="cef28-109">La première technique a tendance à être plus rapide pour les contrôles Win32, mais la seconde est plus rapide pour les contrôles Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="cef28-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="cef28-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cef28-110">See also</span></span>

- [<span data-ttu-id="cef28-111">Obtention d'éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="cef28-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
