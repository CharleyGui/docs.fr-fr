---
title: 'Comment : créer une liaison dans du code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458847"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="760d4-102">Comment : créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="760d4-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="760d4-103">Cet exemple montre comment créer et définir une <xref:System.Windows.Data.Binding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="760d4-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="760d4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="760d4-104">Example</span></span>  
 <span data-ttu-id="760d4-105">La classe <xref:System.Windows.FrameworkElement> et la classe <xref:System.Windows.FrameworkContentElement> exposent toutes deux une méthode `SetBinding`.</span><span class="sxs-lookup"><span data-stu-id="760d4-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="760d4-106">Si vous liez un élément qui hérite de l’une de ces classes, vous pouvez appeler directement la méthode <xref:System.Windows.FrameworkElement.SetBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="760d4-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="760d4-107">L’exemple suivant crée une classe nommée, `MyData`, qui contient une propriété nommée `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="760d4-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="760d4-108">L’exemple suivant montre comment créer un objet de liaison pour définir la source de la liaison.</span><span class="sxs-lookup"><span data-stu-id="760d4-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="760d4-109">L’exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de `myText`, qui est un contrôle <xref:System.Windows.Controls.TextBlock>, à `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="760d4-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="760d4-110">Pour obtenir l’exemple de code complet, consultez [exemple de liaison de code uniquement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="760d4-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="760d4-111">Au lieu d’appeler <xref:System.Windows.FrameworkElement.SetBinding%2A>, vous pouvez utiliser la méthode statique <xref:System.Windows.Data.BindingOperations.SetBinding%2A> de la classe <xref:System.Windows.Data.BindingOperations>.</span><span class="sxs-lookup"><span data-stu-id="760d4-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="760d4-112">L’exemple suivant appelle <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pour lier `myText` à `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="760d4-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="760d4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="760d4-113">See also</span></span>

- [<span data-ttu-id="760d4-114">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="760d4-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="760d4-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="760d4-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
