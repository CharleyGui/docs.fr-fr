---
title: Déclencher des événements à partir d'un fournisseur UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: c973d6ddba498f4bdab4be764a4be6bff1cacf9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966375"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="48561-102">Déclencher des événements à partir d'un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="48561-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="48561-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="48561-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="48561-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="48561-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="48561-105">Cette rubrique contient un exemple de code qui montre comment déclencher un événement à partir d’un fournisseur UI Automation.</span><span class="sxs-lookup"><span data-stu-id="48561-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48561-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="48561-106">Example</span></span>  
 <span data-ttu-id="48561-107">Dans l’exemple suivant, un événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] est déclenché dans l’implémentation d’un contrôle bouton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="48561-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="48561-108">L’implémentation permet à une application client UI Automation de simuler un clic sur un bouton.</span><span class="sxs-lookup"><span data-stu-id="48561-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="48561-109">Pour éviter un traitement inutile, l’exemple examine <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> pour vérifier si des événements doivent être déclenchés.</span><span class="sxs-lookup"><span data-stu-id="48561-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="48561-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48561-110">See also</span></span>

- [<span data-ttu-id="48561-111">Vue d’ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="48561-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
