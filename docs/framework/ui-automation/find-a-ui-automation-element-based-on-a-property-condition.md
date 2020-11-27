---
title: Rechercher un élément UI Automation basé sur une condition de propriété
description: Rechercher un élément UI Automation basé sur une condition de propriété. Localisez un élément dans l’arborescence UI Automation en fonction d’une propriété ou de propriétés spécifiques.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 603ecf5375af919a558168e14792035a16fb20f2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276488"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="3a933-104">Rechercher un élément UI Automation basé sur une condition de propriété</span><span class="sxs-lookup"><span data-stu-id="3a933-104">Find a UI Automation Element Based on a Property Condition</span></span>

> [!NOTE]
> <span data-ttu-id="3a933-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3a933-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3a933-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3a933-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3a933-107">Cette rubrique contient un exemple de code qui montre comment rechercher un élément dans l' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arborescence en fonction d’une propriété ou de propriétés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3a933-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a933-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3a933-108">Example</span></span>  

 <span data-ttu-id="3a933-109">Dans l’exemple suivant, un ensemble de conditions de propriété est spécifié, qui identifient un certain (e) élément (ou) d’intérêt dans l' <xref:System.Windows.Automation.AutomationElement> arborescence.</span><span class="sxs-lookup"><span data-stu-id="3a933-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="3a933-110">Une recherche de tous les éléments correspondants est ensuite effectuée avec la <xref:System.Windows.Automation.AutomationElement.FindAll%2A> méthode qui incorpore une série d' <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.</span><span class="sxs-lookup"><span data-stu-id="3a933-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a933-111">Lors de la recherche à partir du <xref:System.Windows.Automation.AutomationElement.RootElement%2A> , vous devez essayer d’obtenir uniquement les enfants directs.</span><span class="sxs-lookup"><span data-stu-id="3a933-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="3a933-112">Une recherche de descendants peut itérer au sein de centaines, voire de milliers d’éléments, ce qui peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="3a933-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="3a933-113">Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="3a933-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="3a933-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a933-114">See also</span></span>

- <span data-ttu-id="3a933-115">[Exemple d’élément de menu InvokePattern et ExpandCollapsePattern](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a933-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="3a933-116">Obtention d'éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="3a933-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="3a933-117">Utiliser la propriété AutomationID</span><span class="sxs-lookup"><span data-stu-id="3a933-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
