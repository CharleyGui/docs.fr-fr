---
title: Créer un fournisseur UI Automation côté client
description: Consultez un exemple de création d’un fournisseur UI Automation côté client. L’exemple implémente un fournisseur côté client simple pour une fenêtre de console.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: a25966d0f11e409bd4e53f944fc2528360327039
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168475"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="8afb5-104">Créer un fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="8afb5-104">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="8afb5-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="8afb5-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8afb5-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8afb5-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8afb5-107">Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client.</span><span class="sxs-lookup"><span data-stu-id="8afb5-107">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8afb5-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="8afb5-108">Example</span></span>  
 <span data-ttu-id="8afb5-109">L’exemple de code suivant peut être généré dans une bibliothèque de liens dynamiques (DLL) qui implémente un fournisseur côté client très simple pour une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="8afb5-109">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="8afb5-110">Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un assembly de fournisseur pouvant être inscrit par une application cliente UI Automation.</span><span class="sxs-lookup"><span data-stu-id="8afb5-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="8afb5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8afb5-111">See also</span></span>

- [<span data-ttu-id="8afb5-112">Vue d'ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="8afb5-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="8afb5-113">Inscrire un assembly de fournisseur côté client</span><span class="sxs-lookup"><span data-stu-id="8afb5-113">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
