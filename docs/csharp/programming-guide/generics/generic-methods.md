---
title: Méthodes génériques - Guide de programmation C#
description: En savoir plus sur les méthodes déclarées avec des paramètres de type, appelées méthodes génériques. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151465"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="51827-104">Méthodes génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="51827-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="51827-105">Une méthode générique est une méthode qui est déclarée avec des paramètres de type, comme suit :</span><span class="sxs-lookup"><span data-stu-id="51827-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="51827-106">L’exemple de code suivant montre une manière d’appeler la méthode, avec `int` comme argument de type :</span><span class="sxs-lookup"><span data-stu-id="51827-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="51827-107">Vous pouvez également omettre l’argument de type et le compilateur le déduira.</span><span class="sxs-lookup"><span data-stu-id="51827-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="51827-108">L’appel suivant à `Swap` est équivalent à l’appel précédent :</span><span class="sxs-lookup"><span data-stu-id="51827-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="51827-109">Les mêmes règles d’inférence de type s’appliquent aux méthodes statiques et aux méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="51827-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="51827-110">Le compilateur peut déduire les paramètres de type d’après les arguments de méthode que vous passez. Il ne peut pas déduire les paramètres de type uniquement à partir d’une valeur de contrainte ou de retour.</span><span class="sxs-lookup"><span data-stu-id="51827-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="51827-111">Par conséquent, l’inférence de type ne fonctionne pas avec les méthodes qui n’ont pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="51827-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="51827-112">L’inférence de type se produit au moment de la compilation avant que le compilateur n’essaie de résoudre toute signature de méthode surchargée.</span><span class="sxs-lookup"><span data-stu-id="51827-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="51827-113">Le compilateur applique la logique d’inférence de type à toutes les méthodes génériques qui partagent le même nom.</span><span class="sxs-lookup"><span data-stu-id="51827-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="51827-114">À l’étape de résolution de la surcharge, le compilateur inclut uniquement les méthodes génériques sur lesquelles l’inférence de type a réussi.</span><span class="sxs-lookup"><span data-stu-id="51827-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="51827-115">Dans une classe générique, les méthodes non génériques peuvent accéder aux paramètres de type de niveau classe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="51827-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="51827-116">Si vous définissez une méthode générique qui accepte les mêmes paramètres de type que la classe conteneur, le compilateur génère l’avertissement [CS0693](../../misc/cs0693.md), car l’argument fourni à l’intérieur de la portée de la méthode pour le `T` interne masque l’argument fourni pour le `T` externe.</span><span class="sxs-lookup"><span data-stu-id="51827-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="51827-117">Si vous avez éventuellement besoin d’appeler une méthode de classe générique avec des arguments de type différents de ceux qui ont été fournis quand la classe a été instanciée, envisagez de fournir un autre identificateur pour le paramètre de type de la méthode, comme indiqué dans `GenericList2<T>` dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="51827-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="51827-118">Utilisez des contraintes pour permettre des opérations plus spécialisées sur les paramètres de type dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="51827-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="51827-119">Cette version de `Swap<T>`, maintenant appelée `SwapIfGreater<T>`, peut être utilisée avec des arguments de type qui implémentent <xref:System.IComparable%601> uniquement.</span><span class="sxs-lookup"><span data-stu-id="51827-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="51827-120">Les méthodes génériques peuvent être surchargées sur plusieurs paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="51827-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="51827-121">Par exemple, les méthodes suivantes peuvent toutes être dans la même classe :</span><span class="sxs-lookup"><span data-stu-id="51827-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="51827-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="51827-122">C# Language Specification</span></span>  

 <span data-ttu-id="51827-123">Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="51827-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51827-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51827-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="51827-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="51827-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51827-126">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="51827-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="51827-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="51827-127">Methods</span></span>](../classes-and-structs/methods.md)
