---
title: 'Comment : lier les propriétés de deux contrôles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459169"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="524dd-102">Comment : lier les propriétés de deux contrôles</span><span class="sxs-lookup"><span data-stu-id="524dd-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="524dd-103">Cet exemple montre comment lier la propriété d’un contrôle instancié à celle d’un autre à l’aide de la propriété <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="524dd-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="524dd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="524dd-104">Example</span></span>  
 <span data-ttu-id="524dd-105">L’exemple suivant montre comment lier la propriété <xref:System.Windows.Controls.Panel.Background%2A> d’un <xref:System.Windows.Controls.Canvas> au <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="524dd-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="524dd-106">propriété d’un <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="524dd-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="524dd-107">Lors de l’affichage, on obtient un résultat similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="524dd-107">When this example is rendered it looks like the following:</span></span>  
  
![Capture d’écran montrant une zone de liste modifiable avec la valeur vert sélectionnée et un carré vert.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="524dd-109">La propriété de la cible de liaison (dans cet exemple, la propriété <xref:System.Windows.Controls.Panel.Background%2A>) doit être une propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="524dd-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="524dd-110">Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="524dd-110">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524dd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="524dd-111">See also</span></span>

- [<span data-ttu-id="524dd-112">Spécifier la source de liaison</span><span class="sxs-lookup"><span data-stu-id="524dd-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="524dd-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="524dd-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
