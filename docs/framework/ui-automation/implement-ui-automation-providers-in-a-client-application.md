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
ms.openlocfilehash: ef3d03bee412b97ed88ec76e81ad2fd19a9595eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968945"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="0762e-102">Implémenter des fournisseurs UI Automation dans une application cliente</span><span class="sxs-lookup"><span data-stu-id="0762e-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="0762e-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0762e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0762e-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="0762e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0762e-105">Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client dans une application.</span><span class="sxs-lookup"><span data-stu-id="0762e-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="0762e-106">Il s’agit d’un scénario rare.</span><span class="sxs-lookup"><span data-stu-id="0762e-106">This is an uncommon scenario.</span></span> <span data-ttu-id="0762e-107">La plupart du temps, une application de client UI Automation utilise des fournisseurs côté serveur ou des fournisseurs côté client qui résident dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="0762e-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0762e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="0762e-108">Example</span></span>  
 <span data-ttu-id="0762e-109">L’exemple de code suivant implémente un fournisseur simple pour une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="0762e-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="0762e-110">Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un fournisseur dans le code client et de son inscription à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="0762e-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="0762e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0762e-111">See also</span></span>

- [<span data-ttu-id="0762e-112">Vue d’ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="0762e-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="0762e-113">Inscrire un assembly de fournisseur côté client</span><span class="sxs-lookup"><span data-stu-id="0762e-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="0762e-114">Créer un fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="0762e-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="0762e-115">Implémentation de fournisseur UI Automation côté client</span><span class="sxs-lookup"><span data-stu-id="0762e-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
