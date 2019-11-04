---
title: 'Comment : créer une liaison simple'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453511"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="4445f-102">Comment : créer une liaison simple</span><span class="sxs-lookup"><span data-stu-id="4445f-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="4445f-103">Cet exemple montre comment créer un <xref:System.Windows.Data.Binding>simple.</span><span class="sxs-lookup"><span data-stu-id="4445f-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4445f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4445f-104">Example</span></span>  
 <span data-ttu-id="4445f-105">Dans cet exemple, vous avez un objet `Person` avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="4445f-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="4445f-106">L’objet `Person` est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="4445f-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="4445f-107">La ligne surlignée qui contient l’élément `<src>` dans l’exemple suivant instancie l’objet `Person` avec une valeur de propriété `PersonName` de `Joe`.</span><span class="sxs-lookup"><span data-stu-id="4445f-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="4445f-108">Cette opération s’effectue dans la section `Resources` et reçoit une `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="4445f-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="4445f-109">La ligne surlignée qui contient l’élément `<TextBlock>` lie ensuite le contrôle <xref:System.Windows.Controls.TextBlock> à la propriété `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="4445f-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="4445f-110">Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».</span><span class="sxs-lookup"><span data-stu-id="4445f-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4445f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4445f-111">See also</span></span>

- [<span data-ttu-id="4445f-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="4445f-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4445f-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4445f-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
