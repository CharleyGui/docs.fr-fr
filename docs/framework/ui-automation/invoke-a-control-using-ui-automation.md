---
title: Appeler un contrôle à l'aide d'UI Automation
description: Utilisez UI Automation pour rechercher un contrôle correspondant à certaines conditions de propriété, créer un AutomationElement, obtenir un InvokePattern et utiliser Invoke sur le contrôle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 2347a620aab848bf6bcc649a9780aa5a3a520822
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168170"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="3bde5-103">Appeler un contrôle à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="3bde5-103">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="3bde5-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3bde5-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3bde5-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3bde5-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3bde5-106">Cette rubrique montre comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bde5-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="3bde5-107">Rechercher un contrôle qui correspond aux conditions de la propriété spécifique en parcourant la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour l’application cible.</span><span class="sxs-lookup"><span data-stu-id="3bde5-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="3bde5-108">Créer un <xref:System.Windows.Automation.AutomationElement> pour chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="3bde5-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="3bde5-109">Obtenir un objet <xref:System.Windows.Automation.InvokePattern> depuis n’importe quel élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] trouvé qui prend en charge le modèle de contrôle <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="3bde5-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="3bde5-110">Utiliser <xref:System.Windows.Automation.InvokePattern.Invoke%2A> pour appeler le contrôle à partir d’un gestionnaire d’événements client.</span><span class="sxs-lookup"><span data-stu-id="3bde5-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bde5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3bde5-111">Example</span></span>  
 <span data-ttu-id="3bde5-112">Cet exemple utilise la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> de la classe <xref:System.Windows.Automation.AutomationElement> pour générer un objet <xref:System.Windows.Automation.InvokePattern> et appeler un contrôle à l’aide de la méthode <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="3bde5-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="3bde5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bde5-113">See also</span></span>

- [<span data-ttu-id="3bde5-114">Exemple InvokePattern, ExpandCollapsePattern et TogglePattern</span><span class="sxs-lookup"><span data-stu-id="3bde5-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
