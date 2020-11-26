---
title: Accéder au texte à l'aide d'UI Automation
description: Consultez un exemple illustrant comment parcourir le contenu textuel d’un document à l’aide de l’automatisation d’interface utilisateur de Microsoft, par incréments de TextUnit.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 1413cac56e3d6358eb58d55eb2fc0ca583147571
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242030"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="a2194-103">Accéder au texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="a2194-103">Traverse Text Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="a2194-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a2194-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a2194-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a2194-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a2194-106">Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour parcourir le contenu textuel d’un document par incréments <xref:System.Windows.Automation.Text.TextUnit> .</span><span class="sxs-lookup"><span data-stu-id="a2194-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2194-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a2194-107">Example</span></span>  

 <span data-ttu-id="a2194-108">L’exemple de code suivant montre comment parcourir le contenu d’un fournisseur de texte UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a2194-108">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="a2194-109">La méthode <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> déplace les points de terminaison <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> et <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="a2194-109">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="a2194-110">Cette plage de texte est généralement une plage dégénérée représentant le point d’insertion du texte.</span><span class="sxs-lookup"><span data-stu-id="a2194-110">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2194-111">Dans la mesure où seuls les objets incorporés basés sur du texte sont considérés comme faisant partie du flux de texte, les objets incorporés tels que les images n’affectent pas `Move` ou sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a2194-111">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="a2194-112">Toute méthode utilisant <xref:System.Windows.Automation.Text.TextUnit> est différée au prochain <xref:System.Windows.Automation.Text.TextUnit> le plus long pris en charge, si le <xref:System.Windows.Automation.Text.TextUnit> concerné n’est pas pris en charge par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a2194-112">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2194-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2194-113">See also</span></span>

- [<span data-ttu-id="a2194-114">Vue d'ensemble de TextPattern d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="a2194-114">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="a2194-115">Ajouter du contenu à une zone de texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="a2194-115">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="a2194-116">Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="a2194-116">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="a2194-117">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="a2194-117">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a2194-118">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="a2194-118">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
