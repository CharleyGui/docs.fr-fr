---
title: Appeler un contrôle à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 19087cfaa22d166017bcf4e3ce5e6caf73ae5fe5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624550"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="43bd3-102">Appeler un contrôle à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="43bd3-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="43bd3-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="43bd3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="43bd3-104">Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="43bd3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="43bd3-105">Cette rubrique montre comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="43bd3-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="43bd3-106">Rechercher un contrôle qui correspond aux conditions de la propriété spécifique en parcourant la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour l’application cible.</span><span class="sxs-lookup"><span data-stu-id="43bd3-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="43bd3-107">Créer un <xref:System.Windows.Automation.AutomationElement> pour chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="43bd3-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="43bd3-108">Obtenir un objet <xref:System.Windows.Automation.InvokePattern> depuis n’importe quel élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] trouvé qui prend en charge le modèle de contrôle <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="43bd3-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="43bd3-109">Utiliser <xref:System.Windows.Automation.InvokePattern.Invoke%2A> pour appeler le contrôle à partir d’un gestionnaire d’événements client.</span><span class="sxs-lookup"><span data-stu-id="43bd3-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43bd3-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="43bd3-110">Example</span></span>  
 <span data-ttu-id="43bd3-111">Cet exemple utilise la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> de la classe <xref:System.Windows.Automation.AutomationElement> pour générer un objet <xref:System.Windows.Automation.InvokePattern> et appeler un contrôle à l’aide de la méthode <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="43bd3-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="43bd3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43bd3-112">See also</span></span>

- [<span data-ttu-id="43bd3-113">Exemple de TogglePattern InvokePattern et ExpandCollapsePattern</span><span class="sxs-lookup"><span data-stu-id="43bd3-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
