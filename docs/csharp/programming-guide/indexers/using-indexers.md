---
title: Utiliser des indexeurs - Guide de programmation C#
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416237"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="3cdef-102">Utiliser des indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3cdef-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="3cdef-103">Les indexeurs sont une pratique syntaxique qui vous permet de créer une [classe](../../language-reference/keywords/class.md), un [struct](../../language-reference/builtin-types/struct.md)ou une [interface](../../language-reference/keywords/interface.md) que les applications clientes peuvent accéder en tant que tableau.</span><span class="sxs-lookup"><span data-stu-id="3cdef-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="3cdef-104">Le compilateur génère une `Item` propriété (ou une propriété autre que nommée si <xref:System.Runtime.CompilerServices.IndexerNameAttribute> est présent) et les méthodes d’accesseur appropriées.</span><span class="sxs-lookup"><span data-stu-id="3cdef-104">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="3cdef-105">Le plus souvent, les indexeurs sont implémentés dans les types dont l’objectif premier est d’encapsuler une collection ou un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="3cdef-105">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="3cdef-106">Par exemple, supposons que vous ayez une classe `TempRecord` qui représente la température en degrés Fahrenheit enregistrée à 10 heures différentes pendant une période de 24 heures.</span><span class="sxs-lookup"><span data-stu-id="3cdef-106">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="3cdef-107">La classe contient un `temps` tableau de type `float[]` pour stocker les valeurs de température.</span><span class="sxs-lookup"><span data-stu-id="3cdef-107">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="3cdef-108">En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance `TempRecord` sous la forme `float temp = tempRecord[4]` et non sous la forme `float temp = tempRecord.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="3cdef-108">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="3cdef-109">La notation de l’indexeur simplifie non seulement la syntaxe des applications clientes ; elle rend également la classe et son objectif plus intuitifs à comprendre pour d’autres développeurs.</span><span class="sxs-lookup"><span data-stu-id="3cdef-109">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="3cdef-110">Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../language-reference/keywords/this.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3cdef-110">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="3cdef-111">La déclaration d’un indexeur génère automatiquement une propriété nommée `Item` sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="3cdef-111">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="3cdef-112">La `Item` propriété n’est pas directement accessible à partir de l' [expression d’accès au membre](../../language-reference/operators/member-access-operators.md#member-access-expression-)d’instance.</span><span class="sxs-lookup"><span data-stu-id="3cdef-112">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="3cdef-113">En outre, si vous ajoutez votre propre `Item` propriété à un objet avec un indexeur, vous obtiendrez une [Erreur du compilateur CS0102](../../misc/cs0102.md).</span><span class="sxs-lookup"><span data-stu-id="3cdef-113">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="3cdef-114">Pour éviter cette erreur, utilisez l' <xref:System.Runtime.CompilerServices.IndexerNameAttribute> indexeur renommez-le comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3cdef-114">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cdef-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="3cdef-115">Remarks</span></span>

<span data-ttu-id="3cdef-116">Le type d’un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l’indexeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="3cdef-116">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="3cdef-117">Pour plus d’informations sur les niveaux d’accessibilité, consultez [Modificateurs d’accès](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3cdef-117">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="3cdef-118">Pour plus d’informations sur l’utilisation d’indexeurs avec une interface, consultez [Indexeurs d’interface](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="3cdef-118">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="3cdef-119">La signature d’un indexeur est composée du nombre et des types de ses paramètres formels.</span><span class="sxs-lookup"><span data-stu-id="3cdef-119">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="3cdef-120">Elle ne comporte ni le type de l’indexeur ni le nom des paramètres formels.</span><span class="sxs-lookup"><span data-stu-id="3cdef-120">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="3cdef-121">Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="3cdef-121">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="3cdef-122">Une valeur d’indexeur n’est pas classée comme variable ; vous ne pouvez donc pas la passer comme paramètre [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="3cdef-122">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="3cdef-123">Pour affecter à l’indexeur un nom exploitable dans d’autres langages, utilisez <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3cdef-123">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="3cdef-124">Cet indexeur porte le nom `TheItem` , car il est substitué par l’attribut de nom de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="3cdef-124">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="3cdef-125">Par défaut, le nom de l’indexeur est `Item` .</span><span class="sxs-lookup"><span data-stu-id="3cdef-125">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="3cdef-126">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="3cdef-126">Example 1</span></span>

<span data-ttu-id="3cdef-127">L’exemple suivant montre comment déclarer un champ de tableau privé `temps`, et un indexeur.</span><span class="sxs-lookup"><span data-stu-id="3cdef-127">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="3cdef-128">L’indexeur permet d’accéder directement à l’instance `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="3cdef-128">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="3cdef-129">Comme alternative à l’utilisation de l’indexeur, vous pouvez déclarer le tableau comme membre [public](../../language-reference/keywords/public.md) et accéder directement à ses membres, `tempRecord.temps[i]`.</span><span class="sxs-lookup"><span data-stu-id="3cdef-129">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="3cdef-130">Notez que quand l’accès à un indexeur est évalué, par exemple dans une instruction `Console.Write`, l’accesseur [get](../../language-reference/keywords/get.md) est appelé.</span><span class="sxs-lookup"><span data-stu-id="3cdef-130">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="3cdef-131">C’est pourquoi une erreur de compilation se produit s’il n’existe aucun accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="3cdef-131">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="3cdef-132">Indexation avec d’autres valeurs</span><span class="sxs-lookup"><span data-stu-id="3cdef-132">Indexing using other values</span></span>

<span data-ttu-id="3cdef-133">C# ne limite pas le type de paramètre d’indexeur au type entier.</span><span class="sxs-lookup"><span data-stu-id="3cdef-133">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="3cdef-134">Par exemple, il peut être utile d’utiliser une chaîne avec un indexeur.</span><span class="sxs-lookup"><span data-stu-id="3cdef-134">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="3cdef-135">Il est possible d’implémenter un tel indexeur en recherchant la chaîne dans la collection et en retournant la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="3cdef-135">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="3cdef-136">Comme les accesseurs peuvent être surchargés, les versions de chaîne et d’entier peuvent coexister.</span><span class="sxs-lookup"><span data-stu-id="3cdef-136">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="3cdef-137">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="3cdef-137">Example 2</span></span>

<span data-ttu-id="3cdef-138">L’exemple suivant déclare une classe qui stocke les jours de la semaine.</span><span class="sxs-lookup"><span data-stu-id="3cdef-138">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="3cdef-139">Un accesseur `get` prend une chaîne, le nom d’un jour, et retourne l’entier correspondant.</span><span class="sxs-lookup"><span data-stu-id="3cdef-139">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="3cdef-140">Par exemple, « Sunday » retourne 0, « Monday » retourne 1 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="3cdef-140">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="3cdef-141">Utilisation de l’exemple 2</span><span class="sxs-lookup"><span data-stu-id="3cdef-141">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="3cdef-142">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="3cdef-142">Example 3</span></span>

<span data-ttu-id="3cdef-143">L’exemple suivant déclare une classe qui stocke les jours de la semaine à l’aide de l' <xref:System.DayOfWeek?displayProperty=fullName> énumération.</span><span class="sxs-lookup"><span data-stu-id="3cdef-143">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="3cdef-144">Un `get` accesseur prend un `DayOfWeek` , la valeur d’un jour et retourne l’entier correspondant.</span><span class="sxs-lookup"><span data-stu-id="3cdef-144">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="3cdef-145">Par exemple, `DayOfWeek.Sunday` retourne 0, `DayOfWeek.Monday` retourne 1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="3cdef-145">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="3cdef-146">Utilisation de l’exemple 3</span><span class="sxs-lookup"><span data-stu-id="3cdef-146">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="3cdef-147">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="3cdef-147">Robust programming</span></span>

<span data-ttu-id="3cdef-148">La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :</span><span class="sxs-lookup"><span data-stu-id="3cdef-148">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="3cdef-149">N’oubliez pas d’incorporer une stratégie de gestion des erreurs au cas où le code client passerait une valeur d’index non valide.</span><span class="sxs-lookup"><span data-stu-id="3cdef-149">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="3cdef-150">Dans le premier exemple décrit plus haut dans cette rubrique, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l’entrée avant de la passer à l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="3cdef-150">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="3cdef-151">Vous pouvez également placer le code de gestion des erreurs à l’intérieur de l’indexeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="3cdef-151">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="3cdef-152">N’oubliez pas d’indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="3cdef-152">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="3cdef-153">Définissez pour les accesseurs [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) une accessibilité aussi restrictive que possible.</span><span class="sxs-lookup"><span data-stu-id="3cdef-153">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="3cdef-154">Cela est particulièrement important dans le cas de l’accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="3cdef-154">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="3cdef-155">Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="3cdef-155">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cdef-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cdef-156">See also</span></span>

- [<span data-ttu-id="3cdef-157">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3cdef-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3cdef-158">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="3cdef-158">Indexers</span></span>](./index.md)
- [<span data-ttu-id="3cdef-159">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3cdef-159">Properties</span></span>](../classes-and-structs/properties.md)
