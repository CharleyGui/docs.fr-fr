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
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433584"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="3565f-102">Rechercher un élément UI Automation basé sur une condition de propriété</span><span class="sxs-lookup"><span data-stu-id="3565f-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="3565f-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3565f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3565f-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3565f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3565f-105">Cette rubrique contient un exemple de code qui montre comment rechercher un élément dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en fonction d’une propriété ou de propriétés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3565f-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3565f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="3565f-106">Example</span></span>  
 <span data-ttu-id="3565f-107">Dans l’exemple suivant, un ensemble de conditions de propriété est spécifié, qui identifient un certain (e) élément (ou certains) d’intérêt dans l’arborescence <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="3565f-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="3565f-108">Une recherche de tous les éléments correspondants est ensuite effectuée avec la méthode <xref:System.Windows.Automation.AutomationElement.FindAll%2A> qui incorpore une série d’opérations booléennes <xref:System.Windows.Automation.AndCondition> pour limiter le nombre d’éléments correspondants.</span><span class="sxs-lookup"><span data-stu-id="3565f-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3565f-109">Lorsque vous effectuez une recherche à partir de la <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, vous devez essayer d’obtenir uniquement les enfants directs.</span><span class="sxs-lookup"><span data-stu-id="3565f-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="3565f-110">Une recherche de descendants peut itérer au sein de centaines, voire de milliers d’éléments, ce qui peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="3565f-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="3565f-111">Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="3565f-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="3565f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3565f-112">See also</span></span>

- <span data-ttu-id="3565f-113">[Exemple d’élément de menu InvokePattern et ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3565f-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="3565f-114">Obtaining UI Automation Elements</span><span class="sxs-lookup"><span data-stu-id="3565f-114">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="3565f-115">Utiliser la propriété AutomationID</span><span class="sxs-lookup"><span data-stu-id="3565f-115">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
