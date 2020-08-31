---
description: in (modificateur générique) - Référence C#
title: in (modificateur générique) - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118453"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="fa492-103">in (modificateur générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="fa492-103">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="fa492-104">Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="fa492-104">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="fa492-105">Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="fa492-105">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="fa492-106">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="fa492-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="fa492-107">Cela permet la conversion implicite des classes qui implémentent des interfaces contravariantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="fa492-107">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="fa492-108">La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="fa492-108">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="fa492-109">Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique uniquement s’il définit le type des paramètres d’une méthode et non le type de retour d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="fa492-109">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="fa492-110">Les paramètres `In`, `ref` et `out` doivent être invariants, ce qui signifie qu’ils sont ni covariants ni contravariants.</span><span class="sxs-lookup"><span data-stu-id="fa492-110">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="fa492-111">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="fa492-111">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="fa492-112">Par exemple, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez attribuer un objet du type `IComparer<Person>` à un objet du type `IComparer<Employee>` sans utiliser de méthode de conversion spéciale si `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="fa492-112">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="fa492-113">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="fa492-113">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="fa492-114">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="fa492-114">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="fa492-115">Interface générique contravariante</span><span class="sxs-lookup"><span data-stu-id="fa492-115">Contravariant generic interface</span></span>

<span data-ttu-id="fa492-116">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="fa492-116">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="fa492-117">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="fa492-117">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="fa492-118">Délégué générique contravariant</span><span class="sxs-lookup"><span data-stu-id="fa492-118">Contravariant generic delegate</span></span>

<span data-ttu-id="fa492-119">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="fa492-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="fa492-120">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="fa492-120">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="fa492-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="fa492-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fa492-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa492-122">See also</span></span>

- [<span data-ttu-id="fa492-123">à</span><span class="sxs-lookup"><span data-stu-id="fa492-123">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="fa492-124">Covariance et contravariance</span><span class="sxs-lookup"><span data-stu-id="fa492-124">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="fa492-125">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="fa492-125">Modifiers</span></span>](index.md)
