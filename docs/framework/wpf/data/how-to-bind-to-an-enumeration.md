---
title: 'Comment : effectuer une liaison à une énumération'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454443"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="c073e-102">Comment : effectuer une liaison à une énumération</span><span class="sxs-lookup"><span data-stu-id="c073e-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="c073e-103">Cet exemple montre comment effectuer une liaison à une énumération par liaison à la méthode GetValues de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c073e-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c073e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c073e-104">Example</span></span>  
 <span data-ttu-id="c073e-105">Dans l’exemple suivant, la <xref:System.Windows.Controls.ListBox> affiche la liste des valeurs d’énumération <xref:System.Windows.HorizontalAlignment> par le biais de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="c073e-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="c073e-106">Les <xref:System.Windows.Controls.ListBox> et les <xref:System.Windows.Controls.Button> sont liés de telle sorte que vous pouvez modifier la valeur de la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> du <xref:System.Windows.Controls.Button> en sélectionnant une valeur dans le <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c073e-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="c073e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c073e-107">See also</span></span>

- [<span data-ttu-id="c073e-108">Effectuer une liaison à une méthode</span><span class="sxs-lookup"><span data-stu-id="c073e-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="c073e-109">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="c073e-109">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c073e-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="c073e-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
