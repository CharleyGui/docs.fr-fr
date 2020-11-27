---
title: Inscrire un assembly de fournisseur côté client
description: Passez en revue un exemple qui montre comment inscrire une DLL qui contient des fournisseurs UI Automation côté client.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 1c6f7685b796b544925207a22679e6a4da455844
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250461"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="d501f-103">Inscrire un assembly de fournisseur côté client</span><span class="sxs-lookup"><span data-stu-id="d501f-103">Register a Client-Side Provider Assembly</span></span>

> [!NOTE]
> <span data-ttu-id="d501f-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d501f-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d501f-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d501f-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d501f-106">Cette rubrique montre comment inscrire une DLL qui contient des fournisseurs UI Automation côté client.</span><span class="sxs-lookup"><span data-stu-id="d501f-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d501f-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d501f-107">Example</span></span>  

 <span data-ttu-id="d501f-108">L’exemple suivant montre comment inscrire un assembly qui contient un fournisseur pour une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="d501f-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="d501f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d501f-109">See also</span></span>

- [<span data-ttu-id="d501f-110">Créer un fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="d501f-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
