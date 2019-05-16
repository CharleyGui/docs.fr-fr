---
title: Unit, type
description: Découvrez comment la F# 'unit' type est souvent utilisé pour marquer l’emplacement où une valeur est requise par la syntaxe du langage lorsqu’aucune valeur n’est nécessaire ou souhaitée.
ms.date: 05/16/2016
ms.openlocfilehash: d515e19489bfa7de6f17194fd74176cfa0bcd7c9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645123"
---
# <a name="unit-type"></a><span data-ttu-id="ed181-103">Unit, type</span><span class="sxs-lookup"><span data-stu-id="ed181-103">Unit Type</span></span>

<span data-ttu-id="ed181-104">Le `unit` type est un type qui indique l’absence d’une valeur spécifique ; la `unit` type a uniquement une valeur unique, qui agit comme un espace réservé lorsqu’aucune autre valeur n’existe ou n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ed181-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed181-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed181-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="ed181-106">Notes</span><span class="sxs-lookup"><span data-stu-id="ed181-106">Remarks</span></span>

<span data-ttu-id="ed181-107">Chaque F# expression doit correspondre à une valeur.</span><span class="sxs-lookup"><span data-stu-id="ed181-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="ed181-108">Pour les expressions qui ne génèrent pas d’une valeur qui est intéressant, la valeur de type `unit` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ed181-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="ed181-109">Le `unit` type ressemble à la `void` type dans les langages tels que c# et C++.</span><span class="sxs-lookup"><span data-stu-id="ed181-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="ed181-110">Le `unit` type a une valeur unique, et cette valeur est indiquée par le jeton `()`.</span><span class="sxs-lookup"><span data-stu-id="ed181-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="ed181-111">La valeur de la `unit` type est souvent utilisé dans F# programmation pour marquer l’emplacement où une valeur est requise par la syntaxe du langage, mais lorsqu’aucune valeur n’est nécessaire ou souhaitée.</span><span class="sxs-lookup"><span data-stu-id="ed181-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="ed181-112">Un exemple peut être la valeur de retour d’un `printf` (fonction).</span><span class="sxs-lookup"><span data-stu-id="ed181-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="ed181-113">Étant donné que les actions importantes de la `printf` opération se produisent dans la fonction, la fonction n’a pas de retourner une valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="ed181-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="ed181-114">Par conséquent, la valeur de retour est de type `unit`.</span><span class="sxs-lookup"><span data-stu-id="ed181-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="ed181-115">Certaines constructions attendent un `unit` valeur.</span><span class="sxs-lookup"><span data-stu-id="ed181-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="ed181-116">Par exemple, un `do` liaison ou du code au niveau supérieur d’un module est supposée correspondre à un `unit` valeur.</span><span class="sxs-lookup"><span data-stu-id="ed181-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="ed181-117">Le compilateur émet un avertissement lorsqu’un `do` liaison ou du code au niveau supérieur d’un module produit un résultat autre que le `unit` valeur qui n’est pas utilisé, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ed181-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="ed181-118">Cet avertissement est une caractéristique de la programmation fonctionnelle ; Il n’apparaît pas dans les autres langages de programmation .NET.</span><span class="sxs-lookup"><span data-stu-id="ed181-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="ed181-119">Dans un programme purement fonctionnel, dans lequel les fonctions n’ont pas d’effets secondaires, la valeur de retournée finale est le seul résultat d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="ed181-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="ed181-120">Par conséquent, lorsque le résultat est ignoré, il est une erreur de programmation possible.</span><span class="sxs-lookup"><span data-stu-id="ed181-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="ed181-121">Bien que F# n’est pas purement fonctionnels langage de programmation, il est conseillé de suivre le style de programmation fonctionnel chaque fois que possible.</span><span class="sxs-lookup"><span data-stu-id="ed181-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed181-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed181-122">See also</span></span>

- [<span data-ttu-id="ed181-123">Primitive</span><span class="sxs-lookup"><span data-stu-id="ed181-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="ed181-124">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="ed181-124">F# Language Reference</span></span>](index.md)
