---
title: Rechercher un élément UI Automation basé sur une condition de propriété
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 24c236e3d577fd4c9844546b04eefeee9eaf1de8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965143"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="f96ef-102">Rechercher un élément UI Automation basé sur une condition de propriété</span><span class="sxs-lookup"><span data-stu-id="f96ef-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="f96ef-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f96ef-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f96ef-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f96ef-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f96ef-105">Cette rubrique contient un exemple de code qui montre comment rechercher un élément dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] l’arborescence en fonction d’une propriété ou de propriétés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f96ef-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f96ef-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f96ef-106">Example</span></span>  
 <span data-ttu-id="f96ef-107">Dans l’exemple suivant, un ensemble de conditions de propriété est spécifié, qui identifient un certain (e) élément (ou <xref:System.Windows.Automation.AutomationElement> ) d’intérêt dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="f96ef-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="f96ef-108">Une recherche de tous les éléments correspondants est ensuite effectuée avec <xref:System.Windows.Automation.AutomationElement.FindAll%2A> la méthode qui incorpore une série d' <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.</span><span class="sxs-lookup"><span data-stu-id="f96ef-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f96ef-109">Lors de la recherche <xref:System.Windows.Automation.AutomationElement.RootElement%2A>à partir du, vous devez essayer d’obtenir uniquement les enfants directs.</span><span class="sxs-lookup"><span data-stu-id="f96ef-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="f96ef-110">Une recherche de descendants peut itérer au sein de centaines, voire de milliers d’éléments, ce qui peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="f96ef-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="f96ef-111">Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="f96ef-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="f96ef-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f96ef-112">See also</span></span>

- <span data-ttu-id="f96ef-113">[Exemple d’élément de menu InvokePattern et ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f96ef-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="f96ef-114">Obtention d’éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="f96ef-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
- [<span data-ttu-id="f96ef-115">Utiliser la propriété AutomationID</span><span class="sxs-lookup"><span data-stu-id="f96ef-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
