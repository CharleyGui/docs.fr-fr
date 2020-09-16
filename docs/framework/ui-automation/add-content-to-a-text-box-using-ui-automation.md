---
title: Ajouter du contenu à une zone de texte à l'aide d'UI Automation
description: Consultez un exemple d’ajout de contenu dans une zone de texte sur une seule ligne à l’aide de Microsoft UI Automation dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 5e7ab77f1dcc2198e69255013eeb30cc703a235f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543119"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="ef2f3-103">Ajouter du contenu à une zone de texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="ef2f3-103">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="ef2f3-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ef2f3-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="ef2f3-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ef2f3-106">Cette rubrique contient un exemple de code qui montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour insérer du texte dans une zone de texte sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="ef2f3-107">Une autre méthode est fournie pour les contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas applicable.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="ef2f3-108">À des fins de comparaison, l’exemple montre également comment utiliser des méthodes Win32 pour obtenir les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef2f3-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ef2f3-109">Example</span></span>  
 <span data-ttu-id="ef2f3-110">L’exemple suivant montre comment parcourir une séquence de contrôles de texte dans une application cible.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="ef2f3-111">Chaque contrôle de texte est testé pour voir si un <xref:System.Windows.Automation.ValuePattern> objet peut être obtenu à partir de celui-ci à l’aide de la <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="ef2f3-112">Si le contrôle de texte prend en charge <xref:System.Windows.Automation.ValuePattern> , la <xref:System.Windows.Automation.ValuePattern.SetValue%2A> méthode est utilisée pour insérer une chaîne définie par l’utilisateur dans le contrôle de texte.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="ef2f3-113">Dans le cas contraire, la <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> méthode est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ef2f3-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="ef2f3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef2f3-114">See also</span></span>

- <span data-ttu-id="ef2f3-115">[Exemple d’insertion de texte TextPattern](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ef2f3-115">[TextPattern Insert Text Sample](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
