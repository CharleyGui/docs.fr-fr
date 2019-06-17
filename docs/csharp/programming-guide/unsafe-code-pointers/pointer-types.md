---
title: Types pointeur - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 3183f8434dd8a6bc8182e2257d0ab3c7e7c014c4
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833440"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="35256-102">Types pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="35256-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="35256-103">Dans un contexte unsafe, un type peut être un type pointeur, un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="35256-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="35256-104">La déclaration d'un type pointeur peut prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="35256-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="35256-105">Le type spécifié avant `*` dans un type de pointeur est appelé **type référent**.</span><span class="sxs-lookup"><span data-stu-id="35256-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="35256-106">Chacun des types suivants peut être un type référent :</span><span class="sxs-lookup"><span data-stu-id="35256-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="35256-107">Tout type intégral : [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="35256-107">Any integral type: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span></span>
- <span data-ttu-id="35256-108">Tout type à virgule flottante : [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="35256-108">Any floating-point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="35256-109">[char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="35256-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="35256-110">[bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="35256-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="35256-111">[decimal](../../language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="35256-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="35256-112">Tout type [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="35256-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="35256-113">Tout type pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-113">Any pointer type.</span></span> <span data-ttu-id="35256-114">Des expressions comme `void**` sont ainsi autorisées.</span><span class="sxs-lookup"><span data-stu-id="35256-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="35256-115">Tout type struct défini par l'utilisateur qui contient des champs de types unmanaged uniquement.</span><span class="sxs-lookup"><span data-stu-id="35256-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="35256-116">Les types pointeur n’héritent pas de [object](../../language-reference/keywords/object.md), et aucune conversion n’est possible entre les types pointeur et `object`.</span><span class="sxs-lookup"><span data-stu-id="35256-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="35256-117">Par ailleurs, le boxing et l'unboxing ne prennent pas en charge les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="35256-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="35256-118">Cependant, vous pouvez effectuer des conversions entre différents types pointeur ainsi qu'entre des types pointeur et des types intégraux.</span><span class="sxs-lookup"><span data-stu-id="35256-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="35256-119">Lorsque vous déclarez plusieurs pointeurs dans la même déclaration, l'astérisque (\*) est écrit conjointement au type sous-jacent uniquement, il n'est pas utilisé en tant que préfixe de chaque nom de pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="35256-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="35256-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="35256-121">Un pointeur ne peut pas pointer vers une référence ou vers un [struct](../../language-reference/keywords/struct.md) qui contient des références, car une référence d’objet peut être collectée par le récupérateur de mémoire, même si un pointeur pointe vers elle.</span><span class="sxs-lookup"><span data-stu-id="35256-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="35256-122">Le récupérateur de mémoire ne se préoccupe pas de savoir si un objet est pointé par des types pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="35256-123">La valeur de la variable pointeur de type `myType*` est l'adresse d'une variable de type `myType`.</span><span class="sxs-lookup"><span data-stu-id="35256-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="35256-124">Les éléments suivants sont des exemples de déclarations de type pointeur :</span><span class="sxs-lookup"><span data-stu-id="35256-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="35256-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="35256-125">Example</span></span>|<span data-ttu-id="35256-126">Description</span><span class="sxs-lookup"><span data-stu-id="35256-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="35256-127">`p` est un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="35256-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="35256-128">`p` est un pointeur vers un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="35256-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="35256-129">`p` est un tableau unidimensionnel de pointeurs vers des entiers.</span><span class="sxs-lookup"><span data-stu-id="35256-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="35256-130">`p` est un pointeur vers un caractère.</span><span class="sxs-lookup"><span data-stu-id="35256-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="35256-131">`p` est un pointeur vers un type inconnu.</span><span class="sxs-lookup"><span data-stu-id="35256-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="35256-132">L'opérateur d'indirection de pointeur \* peut être utilisé pour accéder au contenu à l'emplacement vers lequel pointe la variable pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="35256-133">Observez par exemple la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="35256-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="35256-134">L'expression `*myVariable` désigne la variable `int` trouvée à l'adresse contenue dans `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="35256-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="35256-135">Plusieurs exemples de pointeurs sont présentés dans les rubriques [fixed, instruction](../../language-reference/keywords/fixed-statement.md) et [Conversions de pointeur](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="35256-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="35256-136">L’exemple suivant utilise le mot clé `unsafe` et les instructions `fixed`, et montre comment incrémenter un pointeur intérieur.</span><span class="sxs-lookup"><span data-stu-id="35256-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="35256-137">Vous pouvez coller ce code dans la fonction Main d'une application console pour l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="35256-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="35256-138">Ces exemples doivent être compilés avec l’ensemble d’options de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="35256-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="35256-139">L'opérateur d'indirection ne peut pas être appliqué à un pointeur de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="35256-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="35256-140">Toutefois, vous pouvez utiliser un cast pour convertir un pointeur void en n'importe quel autre type pointeur, et inversement.</span><span class="sxs-lookup"><span data-stu-id="35256-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="35256-141">Un pointeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="35256-141">A pointer can be `null`.</span></span> <span data-ttu-id="35256-142">Le fait d'appliquer un opérateur d'indirection à un pointeur Null donne lieu à un comportement défini par l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="35256-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="35256-143">Le passage de pointeurs entre méthodes peut engendrer un comportement non défini.</span><span class="sxs-lookup"><span data-stu-id="35256-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="35256-144">Supposons une méthode qui retourne un pointeur à une variable locale par le biais d’un paramètre `in`, `out` ou `ref`, ou comme résultat de fonction.</span><span class="sxs-lookup"><span data-stu-id="35256-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="35256-145">Si le pointeur a été défini dans un bloc fixed, la variable vers laquelle il pointe peut ne plus être fixed.</span><span class="sxs-lookup"><span data-stu-id="35256-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="35256-146">Le tableau suivant répertorie les opérateurs et les instructions qui peuvent fonctionner sur des pointeurs dans un contexte unsafe :</span><span class="sxs-lookup"><span data-stu-id="35256-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="35256-147">Opérateur/Instruction</span><span class="sxs-lookup"><span data-stu-id="35256-147">Operator/Statement</span></span>|<span data-ttu-id="35256-148">Utilisez</span><span class="sxs-lookup"><span data-stu-id="35256-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="35256-149">Exécute l'indirection de pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="35256-150">Accède à un membre d'un struct via un pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="35256-151">Indexe un pointeur.</span><span class="sxs-lookup"><span data-stu-id="35256-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="35256-152">Obtient l'adresse d'une variable.</span><span class="sxs-lookup"><span data-stu-id="35256-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="35256-153">`++` et `--`</span><span class="sxs-lookup"><span data-stu-id="35256-153">`++` and `--`</span></span>|<span data-ttu-id="35256-154">Incrémente et décrémente les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="35256-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="35256-155">`+` et `-`</span><span class="sxs-lookup"><span data-stu-id="35256-155">`+` and `-`</span></span>|<span data-ttu-id="35256-156">Exécute des opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="35256-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="35256-157">`==`, `!=`, `<`, `>`, `<=` et `>=`</span><span class="sxs-lookup"><span data-stu-id="35256-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="35256-158">Compare des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="35256-158">Compares pointers.</span></span>|
|[<span data-ttu-id="35256-159">`stackalloc`, opérateur</span><span class="sxs-lookup"><span data-stu-id="35256-159">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="35256-160">Alloue de la mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="35256-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="35256-161">instruction `fixed`</span><span class="sxs-lookup"><span data-stu-id="35256-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="35256-162">Résout temporairement une variable afin de pouvoir rechercher son adresse.</span><span class="sxs-lookup"><span data-stu-id="35256-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="35256-163">Pour plus d’informations sur les opérateurs associés au pointeur, consultez [Opérateurs associés au pointeur](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="35256-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="35256-164">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="35256-164">C# language specification</span></span>

<span data-ttu-id="35256-165">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="35256-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35256-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35256-166">See also</span></span>

- [<span data-ttu-id="35256-167">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="35256-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35256-168">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="35256-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="35256-169">Conversions de pointeurs</span><span class="sxs-lookup"><span data-stu-id="35256-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="35256-170">Types</span><span class="sxs-lookup"><span data-stu-id="35256-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="35256-171">unsafe</span><span class="sxs-lookup"><span data-stu-id="35256-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
