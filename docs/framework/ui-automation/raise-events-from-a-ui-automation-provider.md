---
title: Déclencher des événements à partir d'un fournisseur UI Automation
description: Consultez un exemple qui montre comment déclencher un événement à partir d’un fournisseur UI Automation. Il déclenche un événement UI Automation dans l’implémentation d’un contrôle bouton personnalisé.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 73be7fd92f3fde90255326c51bed03427fd68e8d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250487"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="dabac-104">Déclencher des événements à partir d'un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="dabac-104">Raise Events from a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="dabac-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="dabac-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dabac-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="dabac-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="dabac-107">Cette rubrique contient un exemple de code qui montre comment déclencher un événement à partir d’un fournisseur UI Automation.</span><span class="sxs-lookup"><span data-stu-id="dabac-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dabac-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="dabac-108">Example</span></span>  

 <span data-ttu-id="dabac-109">Dans l’exemple suivant, un événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] est déclenché dans l’implémentation d’un contrôle bouton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dabac-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="dabac-110">L’implémentation permet à une application client UI Automation de simuler un clic sur un bouton.</span><span class="sxs-lookup"><span data-stu-id="dabac-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="dabac-111">Pour éviter un traitement inutile, l’exemple examine <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> pour vérifier si des événements doivent être déclenchés.</span><span class="sxs-lookup"><span data-stu-id="dabac-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="dabac-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dabac-112">See also</span></span>

- [<span data-ttu-id="dabac-113">Vue d'ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="dabac-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
