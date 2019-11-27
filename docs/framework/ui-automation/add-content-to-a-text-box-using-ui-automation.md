---
title: Ajouter du contenu à une zone de texte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447248"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="28d33-102">Ajouter du contenu à une zone de texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="28d33-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="28d33-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="28d33-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="28d33-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="28d33-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="28d33-105">Cette rubrique contient un exemple de code qui montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour insérer du texte dans une zone de texte sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="28d33-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="28d33-106">Une autre méthode est fournie pour les contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas applicable.</span><span class="sxs-lookup"><span data-stu-id="28d33-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="28d33-107">À des fins de comparaison, l’exemple montre également comment utiliser des méthodes Win32 pour obtenir les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="28d33-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28d33-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="28d33-108">Example</span></span>  
 <span data-ttu-id="28d33-109">L’exemple suivant montre comment parcourir une séquence de contrôles de texte dans une application cible.</span><span class="sxs-lookup"><span data-stu-id="28d33-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="28d33-110">Chaque contrôle de texte est testé pour voir s’il est possible d’obtenir un objet <xref:System.Windows.Automation.ValuePattern> à l’aide de la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>.</span><span class="sxs-lookup"><span data-stu-id="28d33-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="28d33-111">Si le contrôle de texte prend en charge <xref:System.Windows.Automation.ValuePattern>, la méthode <xref:System.Windows.Automation.ValuePattern.SetValue%2A> est utilisée pour insérer une chaîne définie par l’utilisateur dans le contrôle de texte.</span><span class="sxs-lookup"><span data-stu-id="28d33-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="28d33-112">Dans le cas contraire, la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="28d33-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="28d33-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28d33-113">See also</span></span>

- <span data-ttu-id="28d33-114">[Exemple d’insertion de texte TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="28d33-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
