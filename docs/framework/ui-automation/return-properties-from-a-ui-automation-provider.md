---
title: Retourner les propriétés d'un fournisseur UI Automation
description: Découvrez comment un fournisseur UI Automation peut retourner les propriétés d’un élément aux applications clientes dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 14a42c73d1dfb942a7e60ce7a72c3a5aea2b820c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903830"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="3a79d-103">Retourner les propriétés d'un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="3a79d-103">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="3a79d-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3a79d-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3a79d-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3a79d-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3a79d-106">Cette rubrique contient un exemple de code qui montre comment un fournisseur UI Automation peut retourner les propriétés d’un élément aux applications clientes.</span><span class="sxs-lookup"><span data-stu-id="3a79d-106">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="3a79d-107">Pour toute propriété qu’il ne prend pas explicitement en charge, le fournisseur doit retourner `null` (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3a79d-107">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="3a79d-108">Cela garantit qu’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tente d’obtenir la propriété à partir d’une autre source, telle que le fournisseur de fenêtre hôte.</span><span class="sxs-lookup"><span data-stu-id="3a79d-108">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a79d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a79d-109">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="3a79d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a79d-110">See also</span></span>

- [<span data-ttu-id="3a79d-111">Vue d'ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="3a79d-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="3a79d-112">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="3a79d-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
