---
title: "Comment : obtenir l'objet de liaison d'une propriété cible liée aux données"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453050"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="a0982-102">Comment : obtenir l'objet de liaison d'une propriété cible liée aux données</span><span class="sxs-lookup"><span data-stu-id="a0982-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="a0982-103">Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.</span><span class="sxs-lookup"><span data-stu-id="a0982-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="a0982-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0982-104">Example</span></span>
 <span data-ttu-id="a0982-105">Vous pouvez effectuer les opérations suivantes pour récupérer l’objet <xref:System.Windows.Data.Binding> :</span><span class="sxs-lookup"><span data-stu-id="a0982-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="a0982-106">Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="a0982-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="a0982-107">Vous pouvez également récupérer le <xref:System.Windows.Data.BindingExpression>, puis récupérer la valeur de la propriété <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0982-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="a0982-108">Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="a0982-108">For the complete example see [Binding Validation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>

> [!NOTE]
> <span data-ttu-id="a0982-109">Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0982-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0982-110">S’il s’agit d’un <xref:System.Windows.Data.PriorityBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0982-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0982-111">Si vous n’êtes pas certain que la propriété cible est liée à l’aide d’un <xref:System.Windows.Data.Binding>, d’un <xref:System.Windows.Data.MultiBinding>ou d’un <xref:System.Windows.Data.PriorityBinding>, vous pouvez utiliser <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0982-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0982-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0982-112">See also</span></span>

- [<span data-ttu-id="a0982-113">Créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="a0982-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="a0982-114">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="a0982-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
