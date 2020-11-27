---
title: Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation
description: Rechercher et mettre en surbrillance du texte à l’aide d’UI Automation. Un exemple recherche et met en surbrillance séquentiellement chaque occurrence d’une chaîne dans le contenu de contrôle de texte.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: 7ae933bdf12c81e48371fa89ba5fc5cf5dd4731e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276462"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="773a2-104">Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="773a2-104">Find and Highlight Text Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="773a2-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="773a2-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="773a2-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="773a2-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="773a2-107">Cette rubrique montre comment rechercher et mettre en surbrillance séquentiellement chaque occurrence d’une chaîne dans le contenu d’un contrôle de texte à l’aide de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="773a2-107">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="773a2-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="773a2-108">Example</span></span>  

 <span data-ttu-id="773a2-109">L’exemple suivant obtient un <xref:System.Windows.Automation.TextPattern> objet à partir d’un contrôle de texte.</span><span class="sxs-lookup"><span data-stu-id="773a2-109">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="773a2-110">Un <xref:System.Windows.Automation.Text.TextPatternRange> objet, représentant le contenu textuel du document entier, est ensuite créé à l’aide <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> de la propriété de ce <xref:System.Windows.Automation.TextPattern> .</span><span class="sxs-lookup"><span data-stu-id="773a2-110">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="773a2-111">Deux <xref:System.Windows.Automation.Text.TextPatternRange> objets supplémentaires sont ensuite créés pour la fonctionnalité de recherche et de mise en surbrillance séquentielle.</span><span class="sxs-lookup"><span data-stu-id="773a2-111">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="773a2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="773a2-112">See also</span></span>

- [<span data-ttu-id="773a2-113">Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="773a2-113">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
