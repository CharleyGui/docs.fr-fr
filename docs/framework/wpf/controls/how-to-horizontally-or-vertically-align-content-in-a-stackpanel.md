---
title: 'Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel'
description: Découvrez comment ajuster l’orientation du contenu dans un Windows Presentation Foundation StackPanel et la valeur HorizontalAlignment et VerticalAlignment du contenu enfant.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167624"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="4b64f-103">Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel</span><span class="sxs-lookup"><span data-stu-id="4b64f-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="4b64f-104">Cet exemple montre comment ajuster le <xref:System.Windows.Controls.StackPanel.Orientation%2A> de contenu dans un <xref:System.Windows.Controls.StackPanel> élément et comment ajuster le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> du contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="4b64f-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b64f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b64f-105">Example</span></span>  
 <span data-ttu-id="4b64f-106">L’exemple suivant crée trois <xref:System.Windows.Controls.ListBox> éléments dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4b64f-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="4b64f-107">Chaque <xref:System.Windows.Controls.ListBox> représente les valeurs possibles des <xref:System.Windows.Controls.StackPanel.Orientation%2A> Propriétés, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> d’un <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="4b64f-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="4b64f-108">Quand un utilisateur sélectionne une valeur dans l’un des <xref:System.Windows.Controls.ListBox> éléments, la propriété associée du <xref:System.Windows.Controls.StackPanel> et de ses <xref:System.Windows.Controls.Button> éléments enfants changent.</span><span class="sxs-lookup"><span data-stu-id="4b64f-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="4b64f-109">Le fichier code-behind suivant définit les modifications apportées aux événements associés aux <xref:System.Windows.Controls.ListBox> modifications de sélection.</span><span class="sxs-lookup"><span data-stu-id="4b64f-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="4b64f-110"><xref:System.Windows.Controls.StackPanel>est identifié par le <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .</span><span class="sxs-lookup"><span data-stu-id="4b64f-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4b64f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b64f-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="4b64f-112">Vue d'ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="4b64f-112">Panels Overview</span></span>](panels-overview.md)
