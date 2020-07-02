---
title: 'Comment : créer une liaison simple'
description: Créez une liaison simple pour vos applications à l’aide de cet exemple de procédure dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618699"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="75744-103">Comment : créer une liaison simple</span><span class="sxs-lookup"><span data-stu-id="75744-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="75744-104">Cet exemple montre comment créer un simple <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="75744-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75744-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="75744-105">Example</span></span>  
 <span data-ttu-id="75744-106">Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="75744-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="75744-107">L' `Person` objet est défini dans l’espace de noms appelé `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="75744-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="75744-108">La ligne surlignée qui contient l' `<src>` élément dans l’exemple suivant instancie l' `Person` objet avec une `PersonName` valeur de propriété de `Joe` .</span><span class="sxs-lookup"><span data-stu-id="75744-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="75744-109">Cette opération est effectuée dans la `Resources` section et assignée à un `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="75744-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="75744-110">La ligne surlignée qui contient l' `<TextBlock>` élément lie ensuite le <xref:System.Windows.Controls.TextBlock> contrôle à la `PersonName` propriété.</span><span class="sxs-lookup"><span data-stu-id="75744-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="75744-111">En conséquence, le <xref:System.Windows.Controls.TextBlock> s’affiche avec la valeur « Joe ».</span><span class="sxs-lookup"><span data-stu-id="75744-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75744-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75744-112">See also</span></span>

- [<span data-ttu-id="75744-113">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="75744-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="75744-114">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="75744-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
