---
title: Inférence de type
description: Découvrez comment le F# compilateur déduit les types de valeurs, les variables, les paramètres et les valeurs de retour.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630179"
---
# <a name="type-inference"></a><span data-ttu-id="21a8d-103">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="21a8d-103">Type Inference</span></span>

<span data-ttu-id="21a8d-104">Cette rubrique décrit comment le F# compilateur déduit les types de valeurs, de variables, de paramètres et de valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="21a8d-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="21a8d-105">Inférence de type en général</span><span class="sxs-lookup"><span data-stu-id="21a8d-105">Type Inference in General</span></span>

<span data-ttu-id="21a8d-106">L’idée de l’inférence de type est que vous n’avez pas besoin de spécifier F# les types de constructions, sauf lorsque le compilateur ne peut pas déduire le type de façon concluante.</span><span class="sxs-lookup"><span data-stu-id="21a8d-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="21a8d-107">L’omission des informations de type explicite ne signifie F# pas qu’il s’agit d’un langage dynamiquement F# typé ou que les valeurs de sont faiblement typées.</span><span class="sxs-lookup"><span data-stu-id="21a8d-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="21a8d-108">F#est un langage statiquement typé, ce qui signifie que le compilateur déduit un type exact pour chaque construction pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="21a8d-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="21a8d-109">S’il n’y a pas assez d’informations pour que le compilateur déduire les types de chaque construction, vous devez fournir des informations de type supplémentaires, généralement en ajoutant des annotations de type explicites quelque part dans le code.</span><span class="sxs-lookup"><span data-stu-id="21a8d-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="21a8d-110">Inférence des types de paramètres et de retour</span><span class="sxs-lookup"><span data-stu-id="21a8d-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="21a8d-111">Dans une liste de paramètres, vous n’avez pas besoin de spécifier le type de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="21a8d-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="21a8d-112">Et pourtant, F# est un langage typé statiquement, et par conséquent, chaque valeur et expression a un type défini au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="21a8d-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="21a8d-113">Pour les types que vous ne spécifiez pas explicitement, le compilateur déduit le type en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="21a8d-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="21a8d-114">Si le type n’est pas spécifié, il est déduit comme étant générique.</span><span class="sxs-lookup"><span data-stu-id="21a8d-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="21a8d-115">Si le code utilise une valeur de façon incohérente, de façon à ce qu’il n’y ait pas de type déduit unique qui satisfait à toutes les utilisations d’une valeur, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="21a8d-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="21a8d-116">Le type de retour d’une fonction est déterminé par le type de la dernière expression dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="21a8d-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="21a8d-117">Par exemple, dans le code suivant, les `a` types de paramètres et `b` et le type de retour sont `int` tous déduits comme étant `100` , car le `int`littéral est de type.</span><span class="sxs-lookup"><span data-stu-id="21a8d-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="21a8d-118">Vous pouvez influencer l’inférence de type en modifiant les littéraux.</span><span class="sxs-lookup"><span data-stu-id="21a8d-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="21a8d-119">`100` Si vous faites un `uint32` en ajoutant le suffixe `u`, les types de, `a`et `b`sont déduits `uint32`de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="21a8d-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="21a8d-120">Vous pouvez également influencer l’inférence de type à l’aide d’autres constructions qui impliquent des restrictions sur le type, telles que des fonctions et des méthodes qui fonctionnent avec un seul type particulier.</span><span class="sxs-lookup"><span data-stu-id="21a8d-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="21a8d-121">En outre, vous pouvez appliquer des annotations de type explicites à des paramètres de fonction ou de méthode ou à des variables dans des expressions, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="21a8d-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="21a8d-122">Des erreurs sont générées si des conflits se produisent entre différentes contraintes.</span><span class="sxs-lookup"><span data-stu-id="21a8d-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="21a8d-123">Vous pouvez également spécifier explicitement la valeur de retour d’une fonction en fournissant une annotation de type après tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="21a8d-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="21a8d-124">Une annotation de type est souvent utile sur un paramètre lorsque le paramètre est un type d’objet et que vous souhaitez utiliser un membre.</span><span class="sxs-lookup"><span data-stu-id="21a8d-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="21a8d-125">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="21a8d-125">Automatic Generalization</span></span>

<span data-ttu-id="21a8d-126">Si le code de la fonction n’est pas dépendant du type d’un paramètre, le compilateur considère que le paramètre est générique.</span><span class="sxs-lookup"><span data-stu-id="21a8d-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="21a8d-127">C’est ce que l’on appelle la *généralisation automatique*, et il peut s’agir d’une puissante aide à écrire du code générique sans complexité croissante.</span><span class="sxs-lookup"><span data-stu-id="21a8d-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="21a8d-128">Par exemple, la fonction suivante combine deux paramètres de n’importe quel type en un tuple.</span><span class="sxs-lookup"><span data-stu-id="21a8d-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="21a8d-129">Le type est déduit comme étant</span><span class="sxs-lookup"><span data-stu-id="21a8d-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="21a8d-130">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="21a8d-130">Additional Information</span></span>

<span data-ttu-id="21a8d-131">L’inférence de type est décrite plus en détail F# dans la spécification du langage.</span><span class="sxs-lookup"><span data-stu-id="21a8d-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="21a8d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21a8d-132">See also</span></span>

- [<span data-ttu-id="21a8d-133">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="21a8d-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)
