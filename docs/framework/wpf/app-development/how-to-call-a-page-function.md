---
title: Guide pratique pour appeler une fonction de page
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: f170977860a73d339f2d83bc43992e6e2bc4053f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582047"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="47fbb-102">Guide pratique pour appeler une fonction de page</span><span class="sxs-lookup"><span data-stu-id="47fbb-102">How to: Call a Page Function</span></span>
<span data-ttu-id="47fbb-103">Cet exemple montre comment appeler une fonction de page à partir d’une page de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47fbb-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47fbb-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="47fbb-104">Example</span></span>  
 <span data-ttu-id="47fbb-105">Vous pouvez accéder à une fonction de page à l’aide d’un URI (Uniform Resource Identifier), comme vous pouvez le faire lorsque vous accédez à une page.</span><span class="sxs-lookup"><span data-stu-id="47fbb-105">You can navigate to a page function using a uniform resource identifier (URI), just as you can when you navigate to a page.</span></span> <span data-ttu-id="47fbb-106">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="47fbb-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="47fbb-107">Si vous devez passer des données à la fonction de page, vous pouvez créer une instance de celle-ci et passer les données en définissant une propriété.</span><span class="sxs-lookup"><span data-stu-id="47fbb-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="47fbb-108">Ou, comme le montre l’exemple suivant, vous pouvez passer les données à l’aide d’un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="47fbb-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="47fbb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47fbb-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
