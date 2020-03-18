---
title: Délégués avec des méthodes nommées vs anonymes - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712375"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="46917-102">Délégués avec méthodes nommées et méthodes anonymes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="46917-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="46917-103">Un [délégué](../../language-reference/builtin-types/reference-types.md) peut être associé à une méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="46917-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="46917-104">Quand vous instanciez un délégué à l’aide d’une méthode nommée, la méthode est passée en tant que paramètre, par exemple :</span><span class="sxs-lookup"><span data-stu-id="46917-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="46917-105">C’est ce qui s’appelle utiliser une méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="46917-105">This is called using a named method.</span></span> <span data-ttu-id="46917-106">Les délégués construits avec une méthode nommée peuvent encapsuler une méthode [static](../../language-reference/keywords/static.md) ou une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="46917-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="46917-107">Les méthodes nommées représentent la seule façon d’instancier un délégué dans les versions précédentes de C#.</span><span class="sxs-lookup"><span data-stu-id="46917-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="46917-108">Toutefois, dans une situation où la création d’une méthode constitue une charge de travail non souhaitée, C# vous permet d’instancier un délégué et de spécifier immédiatement un bloc de code que le délégué traite quand il est appelé.</span><span class="sxs-lookup"><span data-stu-id="46917-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="46917-109">Le bloc peut contenir une expression lambda ou une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="46917-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="46917-110">Pour plus d’informations, consultez [Fonctions anonymes](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="46917-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46917-111">Notes </span><span class="sxs-lookup"><span data-stu-id="46917-111">Remarks</span></span>  
 <span data-ttu-id="46917-112">La méthode que vous passez en tant que paramètre de délégué doit avoir la même signature que la déclaration du délégué.</span><span class="sxs-lookup"><span data-stu-id="46917-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="46917-113">Une instance de délégué encapsule soit une méthode statique soit une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="46917-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="46917-114">Même si le délégué peut utiliser un paramètre [out](../../language-reference/keywords/out-parameter-modifier.md), nous ne recommandons pas son utilisation avec les délégués d’événement multicast, car vous ne pouvez pas savoir quel délégué sera appelé.</span><span class="sxs-lookup"><span data-stu-id="46917-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="46917-115">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="46917-115">Example 1</span></span>  
 <span data-ttu-id="46917-116">L’exemple suivant est un exemple simple de déclaration et d’utilisation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="46917-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="46917-117">Notez que le délégué, `Del`, et la méthode associée, `MultiplyNumbers`, ont la même signature</span><span class="sxs-lookup"><span data-stu-id="46917-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="46917-118">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="46917-118">Example 2</span></span>  
 <span data-ttu-id="46917-119">Dans l’exemple suivant, un délégué est associé à une méthode statique et à une méthode d’instance, et retourne des informations spécifiques à partir de chacune.</span><span class="sxs-lookup"><span data-stu-id="46917-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="46917-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46917-120">See also</span></span>

- [<span data-ttu-id="46917-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="46917-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="46917-122">Délégués</span><span class="sxs-lookup"><span data-stu-id="46917-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="46917-123">Comment combiner les délégués (délégués multicast)</span><span class="sxs-lookup"><span data-stu-id="46917-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="46917-124">Événements</span><span class="sxs-lookup"><span data-stu-id="46917-124">Events</span></span>](../events/index.md)
