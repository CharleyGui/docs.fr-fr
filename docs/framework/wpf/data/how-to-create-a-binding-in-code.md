---
title: 'Comment : créer une liaison dans du code'
description: Apprenez à créer une liaison dans le code d’une application Windows Presentation Foundation en appelant directement la méthode SetBinding.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165805"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="ffbac-103">Comment : créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="ffbac-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="ffbac-104">Cet exemple montre comment créer et définir un <xref:System.Windows.Data.Binding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="ffbac-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffbac-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ffbac-105">Example</span></span>  
 <span data-ttu-id="ffbac-106">La <xref:System.Windows.FrameworkElement> classe et la <xref:System.Windows.FrameworkContentElement> classe exposent toutes deux une `SetBinding` méthode.</span><span class="sxs-lookup"><span data-stu-id="ffbac-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="ffbac-107">Si vous liez un élément qui hérite de l’une de ces classes, vous pouvez appeler <xref:System.Windows.FrameworkElement.SetBinding%2A> directement la méthode.</span><span class="sxs-lookup"><span data-stu-id="ffbac-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="ffbac-108">L’exemple suivant crée une classe nommée, `MyData` , qui contient une propriété nommée `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="ffbac-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="ffbac-109">L’exemple suivant montre comment créer un objet de liaison pour définir la source de la liaison.</span><span class="sxs-lookup"><span data-stu-id="ffbac-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="ffbac-110">L’exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété de `myText` , qui est un <xref:System.Windows.Controls.TextBlock> contrôle, à `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="ffbac-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="ffbac-111">Pour obtenir l’exemple de code complet, consultez [exemple de liaison de code uniquement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ffbac-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="ffbac-112">Au lieu d’appeler <xref:System.Windows.FrameworkElement.SetBinding%2A> , vous pouvez utiliser la <xref:System.Windows.Data.BindingOperations.SetBinding%2A> méthode statique de la <xref:System.Windows.Data.BindingOperations> classe.</span><span class="sxs-lookup"><span data-stu-id="ffbac-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="ffbac-113">L’exemple suivant appelle <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pour effectuer une liaison `myText` à `myDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="ffbac-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="ffbac-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffbac-114">See also</span></span>

- [<span data-ttu-id="ffbac-115">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="ffbac-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ffbac-116">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="ffbac-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
