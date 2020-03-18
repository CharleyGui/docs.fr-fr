---
title: in (modificateur générique) - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713484"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="b4e3c-102">in (modificateur générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="b4e3c-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="b4e3c-103">Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="b4e3c-104">Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="b4e3c-105">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="b4e3c-106">Cela permet la conversion implicite des classes qui implémentent des interfaces contravariantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="b4e3c-107">La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="b4e3c-108">Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique uniquement s’il définit le type des paramètres d’une méthode et non le type de retour d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="b4e3c-109">Les paramètres `In`, `ref` et `out` doivent être invariants, ce qui signifie qu’ils sont ni covariants ni contravariants.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="b4e3c-110">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="b4e3c-111">Par exemple, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez attribuer un objet du type `IComparer<Person>` à un objet du type `IComparer<Employee>` sans utiliser de méthode de conversion spéciale si `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="b4e3c-112">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="b4e3c-113">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4e3c-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="b4e3c-114">Interface générique contravariante</span><span class="sxs-lookup"><span data-stu-id="b4e3c-114">Contravariant generic interface</span></span>

<span data-ttu-id="b4e3c-115">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="b4e3c-116">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="b4e3c-117">Délégué générique contravariant</span><span class="sxs-lookup"><span data-stu-id="b4e3c-117">Contravariant generic delegate</span></span>

<span data-ttu-id="b4e3c-118">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="b4e3c-119">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="b4e3c-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="b4e3c-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b4e3c-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b4e3c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4e3c-121">See also</span></span>

- [<span data-ttu-id="b4e3c-122">out</span><span class="sxs-lookup"><span data-stu-id="b4e3c-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="b4e3c-123">Covariance et Contravariance</span><span class="sxs-lookup"><span data-stu-id="b4e3c-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b4e3c-124">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="b4e3c-124">Modifiers</span></span>](index.md)
