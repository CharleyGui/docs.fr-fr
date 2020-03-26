---
title: Types pointeur - Guide de programmation C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507033"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="90208-102">Types pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="90208-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="90208-103">Dans un contexte unsafe, un type peut être un type pointeur, un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="90208-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="90208-104">La déclaration d'un type pointeur peut prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="90208-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="90208-105">Le type spécifié avant `*` dans un type de pointeur est appelé **type référent**.</span><span class="sxs-lookup"><span data-stu-id="90208-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="90208-106">Seul un [type non managé](../../language-reference/builtin-types/unmanaged-types.md) peut être un type référent.</span><span class="sxs-lookup"><span data-stu-id="90208-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="90208-107">Les types pointeur n’héritent pas de [object](../../language-reference/builtin-types/reference-types.md), et aucune conversion n’est possible entre les types pointeur et `object`.</span><span class="sxs-lookup"><span data-stu-id="90208-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="90208-108">Par ailleurs, le boxing et l'unboxing ne prennent pas en charge les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="90208-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="90208-109">Cependant, vous pouvez effectuer des conversions entre différents types pointeur ainsi qu'entre des types pointeur et des types intégraux.</span><span class="sxs-lookup"><span data-stu-id="90208-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="90208-110">Lorsque vous déclarez plusieurs pointeurs dans la même déclaration, l'astérisque (\*) est écrit conjointement au type sous-jacent uniquement, il n'est pas utilisé en tant que préfixe de chaque nom de pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="90208-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="90208-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="90208-112">Un pointeur ne peut pas pointer vers une référence ou vers un [struct](../../language-reference/builtin-types/struct.md) qui contient des références, car une référence d’objet peut être collectée par le récupérateur de mémoire, même si un pointeur pointe vers elle.</span><span class="sxs-lookup"><span data-stu-id="90208-112">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="90208-113">Le récupérateur de mémoire ne se préoccupe pas de savoir si un objet est pointé par des types pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="90208-114">La valeur de la variable pointeur de type `myType*` est l'adresse d'une variable de type `myType`.</span><span class="sxs-lookup"><span data-stu-id="90208-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="90208-115">Les éléments suivants sont des exemples de déclarations de type pointeur :</span><span class="sxs-lookup"><span data-stu-id="90208-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="90208-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="90208-116">Example</span></span>|<span data-ttu-id="90208-117">Description</span><span class="sxs-lookup"><span data-stu-id="90208-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="90208-118">`p` est un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="90208-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="90208-119">`p` est un pointeur vers un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="90208-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="90208-120">`p` est un tableau unidimensionnel de pointeurs vers des entiers.</span><span class="sxs-lookup"><span data-stu-id="90208-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="90208-121">`p` est un pointeur vers un caractère.</span><span class="sxs-lookup"><span data-stu-id="90208-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="90208-122">`p` est un pointeur vers un type inconnu.</span><span class="sxs-lookup"><span data-stu-id="90208-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="90208-123">L'opérateur d'indirection de pointeur \* peut être utilisé pour accéder au contenu à l'emplacement vers lequel pointe la variable pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="90208-124">Observez par exemple la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="90208-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="90208-125">L'expression `*myVariable` désigne la variable `int` trouvée à l'adresse contenue dans `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="90208-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="90208-126">Plusieurs exemples de pointeurs sont présentés dans les rubriques [fixed, instruction](../../language-reference/keywords/fixed-statement.md) et [Conversions de pointeur](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="90208-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="90208-127">L’exemple suivant utilise le mot clé `unsafe` et les instructions `fixed`, et montre comment incrémenter un pointeur intérieur.</span><span class="sxs-lookup"><span data-stu-id="90208-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="90208-128">Vous pouvez coller ce code dans la fonction Main d'une application console pour l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="90208-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="90208-129">Ces exemples doivent être compilés avec l’ensemble d’options de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="90208-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="90208-130">L'opérateur d'indirection ne peut pas être appliqué à un pointeur de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="90208-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="90208-131">Toutefois, vous pouvez utiliser un cast pour convertir un pointeur void en n'importe quel autre type pointeur, et inversement.</span><span class="sxs-lookup"><span data-stu-id="90208-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="90208-132">Un pointeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="90208-132">A pointer can be `null`.</span></span> <span data-ttu-id="90208-133">Le fait d'appliquer un opérateur d'indirection à un pointeur Null donne lieu à un comportement défini par l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="90208-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="90208-134">Le passage de pointeurs entre méthodes peut engendrer un comportement non défini.</span><span class="sxs-lookup"><span data-stu-id="90208-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="90208-135">Supposons une méthode qui retourne un pointeur à une variable locale par le biais d’un paramètre `in`, `out` ou `ref`, ou comme résultat de fonction.</span><span class="sxs-lookup"><span data-stu-id="90208-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="90208-136">Si le pointeur a été défini dans un bloc fixed, la variable vers laquelle il pointe peut ne plus être fixed.</span><span class="sxs-lookup"><span data-stu-id="90208-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="90208-137">Le tableau suivant répertorie les opérateurs et les instructions qui peuvent fonctionner sur des pointeurs dans un contexte unsafe :</span><span class="sxs-lookup"><span data-stu-id="90208-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="90208-138">Opérateur/Instruction</span><span class="sxs-lookup"><span data-stu-id="90208-138">Operator/Statement</span></span>|<span data-ttu-id="90208-139">Utilisation</span><span class="sxs-lookup"><span data-stu-id="90208-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="90208-140">Exécute l'indirection de pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="90208-141">Accède à un membre d'un struct via un pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="90208-142">Indexe un pointeur.</span><span class="sxs-lookup"><span data-stu-id="90208-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="90208-143">Obtient l'adresse d'une variable.</span><span class="sxs-lookup"><span data-stu-id="90208-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="90208-144">`++` et `--`</span><span class="sxs-lookup"><span data-stu-id="90208-144">`++` and `--`</span></span>|<span data-ttu-id="90208-145">Incrémente et décrémente les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="90208-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="90208-146">`+` et `-`</span><span class="sxs-lookup"><span data-stu-id="90208-146">`+` and `-`</span></span>|<span data-ttu-id="90208-147">Exécute des opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="90208-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="90208-148">`==`, `!=`, `<`, `>`, `<=` et `>=`</span><span class="sxs-lookup"><span data-stu-id="90208-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="90208-149">Compare des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="90208-149">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="90208-150">Alloue de la mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="90208-150">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="90208-151">`fixed`Déclaration</span><span class="sxs-lookup"><span data-stu-id="90208-151">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="90208-152">Résout temporairement une variable afin de pouvoir rechercher son adresse.</span><span class="sxs-lookup"><span data-stu-id="90208-152">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="90208-153">Pour plus d’informations sur les opérateurs associés au pointeur, consultez [Opérateurs associés au pointeur](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="90208-153">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="90208-154">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="90208-154">C# language specification</span></span>

<span data-ttu-id="90208-155">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="90208-155">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90208-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90208-156">See also</span></span>

- [<span data-ttu-id="90208-157">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="90208-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90208-158">Code et pointeurs dangereux</span><span class="sxs-lookup"><span data-stu-id="90208-158">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="90208-159">Conversions de pointeur</span><span class="sxs-lookup"><span data-stu-id="90208-159">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="90208-160">Types référence</span><span class="sxs-lookup"><span data-stu-id="90208-160">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="90208-161">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="90208-161">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="90208-162">Dangereux</span><span class="sxs-lookup"><span data-stu-id="90208-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
