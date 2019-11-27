---
title: Accéder au texte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 71df7c8f9dde388ffc4445389e105a4ad686539f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441879"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="cdfea-102">Accéder au texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdfea-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="cdfea-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cdfea-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cdfea-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cdfea-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cdfea-105">Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour parcourir le contenu textuel d’un document par incréments <xref:System.Windows.Automation.Text.TextUnit> .</span><span class="sxs-lookup"><span data-stu-id="cdfea-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdfea-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="cdfea-106">Example</span></span>  
 <span data-ttu-id="cdfea-107">L’exemple de code suivant montre comment parcourir le contenu d’un fournisseur de texte UI Automation.</span><span class="sxs-lookup"><span data-stu-id="cdfea-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="cdfea-108">La méthode <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> déplace les points de terminaison <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> et <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="cdfea-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="cdfea-109">Cette plage de texte est généralement une plage dégénérée représentant le point d’insertion du texte.</span><span class="sxs-lookup"><span data-stu-id="cdfea-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdfea-110">Dans la mesure où seuls les objets incorporés basés sur du texte sont considérés comme faisant partie du flux de texte, les objets incorporés tels que les images n’affectent pas `Move` ou sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="cdfea-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="cdfea-111">Toute méthode utilisant <xref:System.Windows.Automation.Text.TextUnit> est différée au prochain <xref:System.Windows.Automation.Text.TextUnit> le plus long pris en charge, si le <xref:System.Windows.Automation.Text.TextUnit> concerné n’est pas pris en charge par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cdfea-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfea-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdfea-112">See also</span></span>

- [<span data-ttu-id="cdfea-113">Vue d’ensemble de TextPattern d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdfea-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="cdfea-114">Ajouter du contenu à une zone de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdfea-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="cdfea-115">Rechercher et mettre en surbrillance le texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdfea-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="cdfea-116">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdfea-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cdfea-117">UI Automation Control Patterns for Clients</span><span class="sxs-lookup"><span data-stu-id="cdfea-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
