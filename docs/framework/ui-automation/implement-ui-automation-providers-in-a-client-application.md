---
title: Implémenter des fournisseurs UI Automation dans une application cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 09b33b78ef8f0b62ef4f1e24c56faae783f1e8dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435470"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="f505d-102">Implémenter des fournisseurs UI Automation dans une application cliente</span><span class="sxs-lookup"><span data-stu-id="f505d-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="f505d-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f505d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f505d-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f505d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f505d-105">Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client dans une application.</span><span class="sxs-lookup"><span data-stu-id="f505d-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="f505d-106">Il s’agit d’un scénario rare.</span><span class="sxs-lookup"><span data-stu-id="f505d-106">This is an uncommon scenario.</span></span> <span data-ttu-id="f505d-107">La plupart du temps, une application de client UI Automation utilise des fournisseurs côté serveur ou des fournisseurs côté client qui résident dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="f505d-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f505d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="f505d-108">Example</span></span>  
 <span data-ttu-id="f505d-109">L’exemple de code suivant implémente un fournisseur simple pour une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f505d-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="f505d-110">Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un fournisseur dans le code client et de son inscription à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="f505d-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="f505d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f505d-111">See also</span></span>

- [<span data-ttu-id="f505d-112">Vue d’ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="f505d-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="f505d-113">Inscrire un assembly de fournisseur côté client</span><span class="sxs-lookup"><span data-stu-id="f505d-113">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="f505d-114">Créer un fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="f505d-114">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="f505d-115">Implémentation de fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="f505d-115">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
