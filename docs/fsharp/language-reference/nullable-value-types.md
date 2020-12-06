---
title: Types valeur Nullable
description: 'Découvrez comment utiliser les types valeur Nullable, un moyen de représenter un type valeur qui peut également être null, en F #.'
ms.date: 11/19/2020
ms.openlocfilehash: da0cd85bd651db81ba98c02a9db31d92dc52a8c6
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740405"
---
# <a name="nullable-value-types"></a><span data-ttu-id="dc38a-103">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="dc38a-103">Nullable value types</span></span>

<span data-ttu-id="dc38a-104">Un _type valeur Nullable_ `Nullable<'T>` représente tout type [struct](structures.md) qui peut également être `null` .</span><span class="sxs-lookup"><span data-stu-id="dc38a-104">A _nullable value type_ `Nullable<'T>` represents any [struct](structures.md) type that could also be `null`.</span></span> <span data-ttu-id="dc38a-105">Cela est utile lors de l’interaction avec des bibliothèques et des composants qui peuvent choisir de représenter ces genres de types, comme des entiers, avec une `null` valeur pour des raisons d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="dc38a-105">This is helpful when interacting with libraries and components that may choose to represent these kinds of types, like integers, with a `null` value for efficiency reasons.</span></span> <span data-ttu-id="dc38a-106">Le type sous-jacent qui stocke cette construction est <xref:System.Nullable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc38a-106">The underlying type that backs this construct is <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc38a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc38a-107">Syntax</span></span>

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a><span data-ttu-id="dc38a-108">Déclarer et assigner avec des valeurs</span><span class="sxs-lookup"><span data-stu-id="dc38a-108">Declare and assign with values</span></span>

<span data-ttu-id="dc38a-109">La déclaration d’un type valeur Nullable est semblable à la déclaration d’un type de type wrapper en F # :</span><span class="sxs-lookup"><span data-stu-id="dc38a-109">Declaring a nullable value type is just like declaring any wrapper-like type in F#:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

<span data-ttu-id="dc38a-110">Vous pouvez également Elide le paramètre de type générique et autoriser l’inférence de type à le résoudre :</span><span class="sxs-lookup"><span data-stu-id="dc38a-110">You can also elide the generic type parameter and allow type inference to resolve it:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

<span data-ttu-id="dc38a-111">Pour assigner à un type valeur Nullable, vous devez également être explicite.</span><span class="sxs-lookup"><span data-stu-id="dc38a-111">To assign to a nullable value type, you'll need to also be explicit.</span></span> <span data-ttu-id="dc38a-112">Il n’existe pas de conversion implicite pour les types valeur Nullable définis en F # :</span><span class="sxs-lookup"><span data-stu-id="dc38a-112">There is no implicit conversion for F#-defined nullable value types:</span></span>

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a><span data-ttu-id="dc38a-113">Affecter une valeur null</span><span class="sxs-lookup"><span data-stu-id="dc38a-113">Assign null</span></span>

<span data-ttu-id="dc38a-114">Vous ne pouvez pas assigner directement `null` à un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="dc38a-114">You cannot directly assign `null` to a nullable value type.</span></span> <span data-ttu-id="dc38a-115">À utiliser à la `Nullable()` place :</span><span class="sxs-lookup"><span data-stu-id="dc38a-115">Use `Nullable()` instead:</span></span>

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

<span data-ttu-id="dc38a-116">Cela est dû au fait que `Nullable<'T>` ne dispose pas `null` de la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="dc38a-116">This is because `Nullable<'T>` does not have `null` as a proper value.</span></span>

## <a name="pass-and-assign-to-members"></a><span data-ttu-id="dc38a-117">Passer et assigner à des membres</span><span class="sxs-lookup"><span data-stu-id="dc38a-117">Pass and assign to members</span></span>

<span data-ttu-id="dc38a-118">La principale différence entre l’utilisation des membres et des valeurs F # est que les types valeur Nullable peuvent être implicitement déduits lorsque vous utilisez des membres.</span><span class="sxs-lookup"><span data-stu-id="dc38a-118">A key difference between working with members and F# values is that nullable value types can be implicitly inferred when you're working with members.</span></span> <span data-ttu-id="dc38a-119">Considérez la méthode folling qui accepte un type valeur Nullable comme entrée :</span><span class="sxs-lookup"><span data-stu-id="dc38a-119">Consider the folling method that takes a nullable value type as input:</span></span>

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

<span data-ttu-id="dc38a-120">Dans l’exemple précédent, vous pouvez passer `12` à la méthode `M` .</span><span class="sxs-lookup"><span data-stu-id="dc38a-120">In the previous example, you can pass `12` to the method `M`.</span></span> <span data-ttu-id="dc38a-121">Vous pouvez également assigner `12` à la propriété auto `NVT` .</span><span class="sxs-lookup"><span data-stu-id="dc38a-121">You can also assign `12` to the auto property `NVT`.</span></span> <span data-ttu-id="dc38a-122">Le compilateur F # convertit implicitement un appel ou une assignation comme suit lorsque le type cible correspond à l’entrée, si l’entrée peut être construite comme un type de valeur nullabel.</span><span class="sxs-lookup"><span data-stu-id="dc38a-122">The F# compiler will implicitly convert a call or assignment like this when the target type matches the input, if the input can be constructed as a nullabel value type.</span></span>

## <a name="examine-a-nullable-value-type-instance"></a><span data-ttu-id="dc38a-123">Examiner une instance de type valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="dc38a-123">Examine a nullable value type instance</span></span>

<span data-ttu-id="dc38a-124">Contrairement aux [options](options.md), qui sont une construction généralisée pour représenter une valeur possible, les types valeur Nullable ne sont pas utilisés avec les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="dc38a-124">Unlike [Options](options.md), which are a generalized construct for representing a possible value, nullable value types are not used with pattern matching.</span></span> <span data-ttu-id="dc38a-125">Au lieu de cela, vous devez utiliser une [`if`](conditional-expressions-if-then-else.md) expression et vérifier la `HasValue` propriété.</span><span class="sxs-lookup"><span data-stu-id="dc38a-125">Instead, you need to use an [`if`](conditional-expressions-if-then-else.md) expression and check the `HasValue` property.</span></span>

<span data-ttu-id="dc38a-126">Pour obtenir la valeur sous-jacente, utilisez la `Value` propriété après une `HasValue` vérification, comme suit :</span><span class="sxs-lookup"><span data-stu-id="dc38a-126">To get the underlying value, use the `Value` property after a `HasValue` check, like so:</span></span>

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a><span data-ttu-id="dc38a-127">Opérateurs Nullable</span><span class="sxs-lookup"><span data-stu-id="dc38a-127">Nullable operators</span></span>

<span data-ttu-id="dc38a-128">Les opérations sur les types valeur Nullable, telles que l’arithmétique ou la comparaison, peuvent nécessiter l’utilisation d' [opérateurs Nullable](symbol-and-operator-reference/nullable-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc38a-128">Operations on nullable value types, such as arithmetic or comparison, can require the use of [nullable operators](symbol-and-operator-reference/nullable-operators.md).</span></span>

<span data-ttu-id="dc38a-129">Vous pouvez convertir un type valeur Nullable en un autre à l’aide des opérateurs de conversion de l' `FSharp.Linq` espace de noms :</span><span class="sxs-lookup"><span data-stu-id="dc38a-129">You can convert from one nullable value type to another using conversion operators from the `FSharp.Linq` namespace:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

<span data-ttu-id="dc38a-130">Vous pouvez également utiliser un opérateur non Nullable approprié pour effectuer une conversion vers un type primitif, ce qui risque d’être une exception s’il n’a pas de valeur :</span><span class="sxs-lookup"><span data-stu-id="dc38a-130">You can also use an appropriate non-nullable operator to convert to a primitive type, risking an exception if it has no value:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

<span data-ttu-id="dc38a-131">Vous pouvez également utiliser des opérateurs Nullable comme un raccourci pour vérifier `HasValue` et `Value` :</span><span class="sxs-lookup"><span data-stu-id="dc38a-131">You can also use nullable operators as a short-hand for checking `HasValue` and `Value`:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

<span data-ttu-id="dc38a-132">La `?>` comparaison vérifie si le côté gauche est Nullable et s’il a une valeur uniquement si elle a une valeur.</span><span class="sxs-lookup"><span data-stu-id="dc38a-132">The `?>` comparison checks if the left-hand side is nullable and only succeeds if it has a value.</span></span> <span data-ttu-id="dc38a-133">Elle est équivalente à la ligne qui la suit.</span><span class="sxs-lookup"><span data-stu-id="dc38a-133">It is equivalent to the line that follows it.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc38a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc38a-134">See also</span></span>

- [<span data-ttu-id="dc38a-135">Structures</span><span class="sxs-lookup"><span data-stu-id="dc38a-135">Structures</span></span>](structures.md)
- [<span data-ttu-id="dc38a-136">Options F #</span><span class="sxs-lookup"><span data-stu-id="dc38a-136">F# Options</span></span>](options.md)
