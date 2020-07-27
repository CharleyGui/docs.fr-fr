---
title: S'abonner à des événements UI Automation
description: Consultez Comment s’abonner aux événements déclenchés par les fournisseurs UI Automation. L’exemple de code inscrit un gestionnaire d’événements pour l’événement déclenché quand un contrôle est appelé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163534"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="c0f80-104">S'abonner à des événements UI Automation</span><span class="sxs-lookup"><span data-stu-id="c0f80-104">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="c0f80-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c0f80-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c0f80-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c0f80-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c0f80-107">Cette rubrique montre comment s’abonner à des événements déclenchés par des fournisseurs UI Automation.</span><span class="sxs-lookup"><span data-stu-id="c0f80-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0f80-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0f80-108">Example</span></span>  
 <span data-ttu-id="c0f80-109">L’exemple de code suivant inscrit un gestionnaire d’événements pour l’événement qui est déclenché quand un contrôle tel qu’un bouton est appelé, et le supprime à la fermeture du formulaire d’application.</span><span class="sxs-lookup"><span data-stu-id="c0f80-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="c0f80-110">L’événement est identifié par un <xref:System.Windows.Automation.AutomationEvent> passé comme paramètre à <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f80-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="c0f80-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0f80-111">Example</span></span>  
 <span data-ttu-id="c0f80-112">L’exemple suivant montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour s’abonner à un événement déclenché quand le focus est modifié.</span><span class="sxs-lookup"><span data-stu-id="c0f80-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="c0f80-113">L’inscription du gestionnaire d’événements est annulée dans une méthode qui peut être appelée à l’arrêt de l’application, ou quand la notification d’événements d’interface utilisateur n’est plus obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c0f80-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="c0f80-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0f80-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="c0f80-115">Vue d'ensemble des événements UI Automation</span><span class="sxs-lookup"><span data-stu-id="c0f80-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
