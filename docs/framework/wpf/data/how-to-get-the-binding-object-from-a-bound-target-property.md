---
title: 'Procédure : Obtenir l’objet de liaison d’une propriété cible liée aux données'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965435"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="89f42-102">Procédure : Obtenir l’objet de liaison d’une propriété cible liée aux données</span><span class="sxs-lookup"><span data-stu-id="89f42-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="89f42-103">Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.</span><span class="sxs-lookup"><span data-stu-id="89f42-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f42-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="89f42-104">Example</span></span>  
 <span data-ttu-id="89f42-105">Vous pouvez effectuer les opérations suivantes pour récupérer <xref:System.Windows.Data.Binding> l’objet:</span><span class="sxs-lookup"><span data-stu-id="89f42-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> <span data-ttu-id="89f42-106">Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="89f42-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="89f42-107">Vous pouvez également récupérer <xref:System.Windows.Data.BindingExpression> , puis récupérer la valeur de la <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="89f42-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="89f42-108">Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="89f42-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f42-109">Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="89f42-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="89f42-110">S’il s’agit <xref:System.Windows.Data.PriorityBinding>d’un <xref:System.Windows.Data.BindingOperations>,<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>utilisez..</span><span class="sxs-lookup"><span data-stu-id="89f42-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="89f42-111">Si vous n’êtes pas certain que la propriété cible est liée <xref:System.Windows.Data.Binding>à l' <xref:System.Windows.Data.MultiBinding>aide d’un <xref:System.Windows.Data.PriorityBinding>, d’un ou <xref:System.Windows.Data.BindingOperations>d'<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>un, vous pouvez utiliser..</span><span class="sxs-lookup"><span data-stu-id="89f42-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f42-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89f42-112">See also</span></span>

- [<span data-ttu-id="89f42-113">Créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="89f42-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="89f42-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="89f42-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
