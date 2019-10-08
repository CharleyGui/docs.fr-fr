---
title: In (modificateur générique)-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004871"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="168f1-102">In (modificateur générique) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="168f1-102">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="168f1-103">Pour les paramètres de type générique, le mot clé `In` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="168f1-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="168f1-104">Notes</span><span class="sxs-lookup"><span data-stu-id="168f1-104">Remarks</span></span>

<span data-ttu-id="168f1-105">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="168f1-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="168f1-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="168f1-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="168f1-107">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="168f1-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="168f1-108">Règles</span><span class="sxs-lookup"><span data-stu-id="168f1-108">Rules</span></span>

<span data-ttu-id="168f1-109">Vous pouvez utiliser le mot clé `In` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="168f1-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="168f1-110">Un paramètre de type peut être déclaré contravariant dans une interface ou un délégué générique s’il est utilisé uniquement comme type d’arguments de méthode et qu’il n’est pas utilisé comme type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="168f1-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="168f1-111">les paramètres `ByRef` ne peuvent pas être covariants ou contravariants.</span><span class="sxs-lookup"><span data-stu-id="168f1-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="168f1-112">La covariance et la contravariance sont prises en charge pour les types référence et ne sont pas prises en charge pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="168f1-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="168f1-113">Dans Visual Basic, vous ne pouvez pas déclarer d’événements dans les interfaces contravariant sans spécifier le type délégué.</span><span class="sxs-lookup"><span data-stu-id="168f1-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="168f1-114">En outre, les interfaces contravariant ne peuvent pas avoir de classes imbriquées, d’énumérations ou de structures, mais elles peuvent avoir des interfaces imbriquées.</span><span class="sxs-lookup"><span data-stu-id="168f1-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="168f1-115">Comportement</span><span class="sxs-lookup"><span data-stu-id="168f1-115">Behavior</span></span>

<span data-ttu-id="168f1-116">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="168f1-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="168f1-117">Par exemple, étant donné que dans .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="168f1-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="168f1-118">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="168f1-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="168f1-119">Exemple : interface générique contravariant</span><span class="sxs-lookup"><span data-stu-id="168f1-119">Example - contravariant generic interface</span></span>

<span data-ttu-id="168f1-120">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="168f1-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="168f1-121">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="168f1-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="168f1-122">Exemple : délégué générique contravariant</span><span class="sxs-lookup"><span data-stu-id="168f1-122">Example - contravariant generic delegate</span></span>

<span data-ttu-id="168f1-123">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="168f1-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="168f1-124">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="168f1-124">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="168f1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="168f1-125">See also</span></span>

- [<span data-ttu-id="168f1-126">Variance dans les interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="168f1-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="168f1-127">Out</span><span class="sxs-lookup"><span data-stu-id="168f1-127">Out</span></span>](out-generic-modifier.md)
