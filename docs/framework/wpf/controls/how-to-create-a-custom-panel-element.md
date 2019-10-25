---
title: 'Comment : créer un élément Panel personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799149"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="b4fc7-102">Comment : créer un élément Panel personnalisé</span><span class="sxs-lookup"><span data-stu-id="b4fc7-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="b4fc7-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4fc7-103">Example</span></span>  
 <span data-ttu-id="b4fc7-104">Cet exemple montre comment substituer le comportement de disposition par défaut de l’élément <xref:System.Windows.Controls.Panel> et créer des éléments de disposition personnalisés dérivés de <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="b4fc7-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="b4fc7-105">L’exemple définit un élément <xref:System.Windows.Controls.Panel> personnalisé simple appelé `PlotPanel`, qui positionne des éléments enfants en fonction de deux coordonnées x et y codées en dur.</span><span class="sxs-lookup"><span data-stu-id="b4fc7-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="b4fc7-106">Dans cet exemple, `x` et `y` ont tous les deux la valeur `50`; par conséquent, tous les éléments enfants sont positionnés à cet emplacement sur les axes x et y.</span><span class="sxs-lookup"><span data-stu-id="b4fc7-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="b4fc7-107">Pour implémenter des comportements de <xref:System.Windows.Controls.Panel> personnalisés, l’exemple utilise les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4fc7-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="b4fc7-108">Chaque méthode retourne les données <xref:System.Windows.Size> nécessaires pour positionner et restituer les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="b4fc7-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b4fc7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4fc7-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="b4fc7-110">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="b4fc7-110">Panels Overview</span></span>](panels-overview.md)
