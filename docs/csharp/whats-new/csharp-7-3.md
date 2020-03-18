---
title: Nouveautés de C# 7.3
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204560"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="ffa5b-103">Nouveautés de C# 7.3</span><span class="sxs-lookup"><span data-stu-id="ffa5b-103">What's new in C# 7.3</span></span>

<span data-ttu-id="ffa5b-104">Il existe deux thèmes principaux pour la version C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="ffa5b-105">Un thème fournit des fonctionnalités permettant au code sécurisé d’être aussi performant que le code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="ffa5b-106">Le second thème fournit des améliorations incrémentielles aux fonctionnalités existantes.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="ffa5b-107">En outre, de nouvelles options de compilateur ont été ajoutées à cette version.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="ffa5b-108">Les nouvelles fonctionnalités suivantes prennent en charge le thème de meilleures performances pour le code sécurisé :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="ffa5b-109">Vous pouvez accéder à des champs fixes sans épinglage.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="ffa5b-110">Vous pouvez réaffecter des variables locales `ref`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="ffa5b-111">Vous pouvez utiliser des initialiseurs sur les tableaux `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="ffa5b-112">Vous pouvez utiliser des instructions `fixed` avec tout type prenant en charge un modèle.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="ffa5b-113">Vous pouvez utiliser des contraintes génériques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="ffa5b-114">Les améliorations suivantes ont été apportées aux fonctionnalités existantes :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="ffa5b-115">Vous pouvez tester `==` et `!=` avec des types de tuple.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="ffa5b-116">Vous pouvez utiliser des variables d’expression dans d’autres emplacements.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="ffa5b-117">Vous pouvez joindre des attributs à un champ de stockage de propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="ffa5b-118">La résolution de la méthode lorsque des arguments diffèrent de `in` a été améliorée.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="ffa5b-119">La résolution de la surcharge comporte maintenant moins de cas ambigus.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="ffa5b-120">Les nouvelles options du compilateur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-120">The new compiler options are:</span></span>

- <span data-ttu-id="ffa5b-121">`-publicsign` pour activer la signature d’assemblys Open Source Software (OSS).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="ffa5b-122">`-pathmap` pour fournir un mappage des répertoires sources.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="ffa5b-123">Le reste de cet article fournit des détails et des liens pour en savoir plus sur chacune de ces améliorations.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="ffa5b-124">Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ffa5b-125">Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="ffa5b-126">Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ffa5b-127">Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ffa5b-128">Exécutez `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="ffa5b-129">Code sécurisé plus performant</span><span class="sxs-lookup"><span data-stu-id="ffa5b-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="ffa5b-130">Vous devez être en mesure d’écrire en toute sécurité un code C# ainsi performant qu’un code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="ffa5b-131">Le code sécurisé évite les classes d’erreurs, par exemple les dépassements de mémoire tampon, les pointeurs perdus et d’autres erreurs d’accès à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="ffa5b-132">Ces nouvelles fonctionnalités étendent les fonctionnalités de code sécurisé vérifiables.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="ffa5b-133">Efforcez-vous d’utiliser plus de constructions sécurisées pour écrire votre code.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="ffa5b-134">Ces fonctionnalités facilitent cette écriture.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="ffa5b-135">L’indexation des champs `fixed` ne nécessite aucun épinglage</span><span class="sxs-lookup"><span data-stu-id="ffa5b-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="ffa5b-136">Prenons le struct suivant :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="ffa5b-137">Dans les versions antérieures de C#, vous deviez épingler une variable pour accéder à un des entiers faisant partie de `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="ffa5b-138">À présent, le code suivant se compile sans épingler la variable `p` à l’intérieur d’une instruction `fixed` distincte :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="ffa5b-139">La variable `p` accède à un élément dans `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="ffa5b-140">Vous n’avez pas besoin de déclarer une variable `int*` distincte.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="ffa5b-141">Notez que vous avez toujours besoin d’un contexte `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="ffa5b-142">Dans les versions antérieures de C#, vous devez déclarer un second pointeur fixe :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="ffa5b-143">Pour plus d’informations, [ `fixed` ](../language-reference/keywords/fixed-statement.md)voir l’article sur la déclaration .</span><span class="sxs-lookup"><span data-stu-id="ffa5b-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="ffa5b-144">Les variables locales `ref` peuvent être réaffectées</span><span class="sxs-lookup"><span data-stu-id="ffa5b-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="ffa5b-145">Désormais, les variables locales `ref` peuvent être réassignées pour faire référence à d’autres instances, après avoir été initialisées.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="ffa5b-146">Le code suivant effectue maintenant une compilation :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="ffa5b-147">Pour plus d’informations, voir l’article sur [`foreach`](../language-reference/keywords/foreach-in.md) [ `ref` les retours et `ref` les habitants](../programming-guide/classes-and-structs/ref-returns.md), et l’article sur .</span><span class="sxs-lookup"><span data-stu-id="ffa5b-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="ffa5b-148">Les tableaux `stackalloc` prennent en charge les initialiseurs</span><span class="sxs-lookup"><span data-stu-id="ffa5b-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="ffa5b-149">Vous avez été en mesure de spécifier les valeurs des éléments dans un tableau lors de son initialisation :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="ffa5b-150">Maintenant, la même syntaxe peut être appliquée aux tableaux déclarés avec `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="ffa5b-151">Pour plus d’informations, voir l’article de [ `stackalloc` l’opérateur.](../language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="ffa5b-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="ffa5b-152">D’autres types prennent en charge l’instruction `fixed`</span><span class="sxs-lookup"><span data-stu-id="ffa5b-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="ffa5b-153">L’instruction `fixed` prenait en charge un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="ffa5b-154">À partir de C# 7.3, tout type contenant une méthode `GetPinnableReference()` qui retourne `ref T` ou `ref readonly T` peut être `fixed`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="ffa5b-155">L’ajout de cette fonctionnalité signifie que `fixed` peut être utilisé avec <xref:System.Span%601?displayProperty=nameWithType> et des types connexes.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="ffa5b-156">Pour plus d’informations, voir l’article [ `fixed` de déclaration](../language-reference/keywords/fixed-statement.md) dans la référence linguistique.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="ffa5b-157">Contraintes génériques améliorées</span><span class="sxs-lookup"><span data-stu-id="ffa5b-157">Enhanced generic constraints</span></span>

<span data-ttu-id="ffa5b-158">Vous pouvez maintenant spécifier le type <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> en tant que contraintes de classe de base pour un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="ffa5b-159">Vous pouvez également `unmanaged` utiliser la nouvelle contrainte, pour spécifier qu’un paramètre de type doit être un type non-nullable [non gestion .](../language-reference/builtin-types/unmanaged-types.md)</span><span class="sxs-lookup"><span data-stu-id="ffa5b-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="ffa5b-160">Pour plus d’informations, [ `where` ](../language-reference/keywords/where-generic-type-constraint.md) voir les articles sur les contraintes [génériques](../programming-guide/generics/constraints-on-type-parameters.md)et les contraintes sur les paramètres de type .</span><span class="sxs-lookup"><span data-stu-id="ffa5b-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="ffa5b-161">L’ajout de ces contraintes aux types existants est une [modification incompatible](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ffa5b-162">Les types génériques fermés peuvent ne plus respecter ces nouvelles contraintes.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="ffa5b-163">Améliorer les fonctionnalités existantes</span><span class="sxs-lookup"><span data-stu-id="ffa5b-163">Make existing features better</span></span>

<span data-ttu-id="ffa5b-164">Le second thème fournit des améliorations apportées aux fonctionnalités du langage.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="ffa5b-165">Ces fonctionnalités améliorent la productivité lors de l’écriture de code C#.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="ffa5b-166">Les tuples prennent en charge `==` et `!=`</span><span class="sxs-lookup"><span data-stu-id="ffa5b-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="ffa5b-167">Les types tuple C# prennent désormais en charge `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="ffa5b-168">Pour plus d’informations, consultez la section consacrée à [l’égalité](../tuples.md#equality-and-tuples) dans l’article sur les [tuples](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="ffa5b-169">Joindre des attributs à des champs de stockage pour les propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="ffa5b-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="ffa5b-170">Cette syntaxe est maintenant prise en charge :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="ffa5b-171">L’attribut `SomeThingAboutFieldAttribute` est appliqué au champ de stockage généré par le compilateur pour `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="ffa5b-172">Pour plus d’informations, consultez les [attributs](../programming-guide/concepts/attributes/index.md) dans le guide de programmation C#.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="ffa5b-173">`in` critère de résolution de surcharge de méthode</span><span class="sxs-lookup"><span data-stu-id="ffa5b-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="ffa5b-174">Lorsque le modificateur de l’argument `in` a été ajouté, ces deux méthodes provoqueraient une ambiguïté :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="ffa5b-175">À présent, la surcharge par valeur (la première dans l’exemple précédent) est meilleure que la version de référence en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="ffa5b-176">Pour appeler la version avec l’argument de référence en lecture seule, vous devez inclure le modificateur `in` lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="ffa5b-177">Cette opération a été implémentée en tant que correctif de bogue.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="ffa5b-178">Il n’y a donc plus d’ambiguïté, même si la version du langage est définie sur « 7.2 ».</span><span class="sxs-lookup"><span data-stu-id="ffa5b-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="ffa5b-179">Pour plus d’informations, voir l’article sur le [ `in` modificateur de paramètres](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="ffa5b-180">Étendre des variables d’expression dans les initialiseurs</span><span class="sxs-lookup"><span data-stu-id="ffa5b-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="ffa5b-181">La syntaxe ajoutée dans C# 7.0 pour autoriser les déclarations variables `out` a été étendue pour inclure des initialiseurs de champ, des initialiseurs de propriété, des initialiseurs de constructeur et des clauses de requête.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="ffa5b-182">Il permet d’écrire un code tel que l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-182">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="ffa5b-183">Candidats de surcharge améliorés</span><span class="sxs-lookup"><span data-stu-id="ffa5b-183">Improved overload candidates</span></span>

<span data-ttu-id="ffa5b-184">Dans chaque version, les règles de résolution de surcharge ont été mises à jour pour résoudre les situations où des appels de méthode ambigus sont face à un choix « évident ».</span><span class="sxs-lookup"><span data-stu-id="ffa5b-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="ffa5b-185">Cette version ajoute trois nouvelles règles pour aider le compilateur à opter pour le choix évident :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="ffa5b-186">Lorsqu’un groupe de méthodes contient à la fois une instance et des membres statiques, le compilateur ignore les membres de l’instance si la méthode a été appelée sans récepteur d’instance ou contexte.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="ffa5b-187">Le compilateur ignore les membres statiques si la méthode a été appelée avec un récepteur d’instance.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="ffa5b-188">Lorsqu’il n’existe aucun récepteur, le compilateur inclut uniquement les membres statiques dans un contexte statique, sinon, à la fois les membres statiques et les membres de l’instance.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="ffa5b-189">Lorsque le récepteur représente de façon ambiguë une instance ou un type, le compilateur inclut les deux éléments.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="ffa5b-190">Un contexte statique, où un récepteur d’instance `this` implicite ne peut pas être utilisé, inclut le corps des membres où aucun `this` n’est défini, par exemple des membres statiques, ainsi que chaque endroit où `this` ne peut pas être utilisé, par exemple les initialiseurs de champ et les initialiseurs de constructeur.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="ffa5b-191">Lorsqu’un groupe de méthodes contient certaines méthodes génériques dont les arguments de type ne répondent pas à leurs contraintes, ces membres sont supprimés de l’ensemble de candidats.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="ffa5b-192">Pour une conversion de groupe de méthodes, les méthodes candidates dont le type de retour ne correspond pas à celui du délégué sont supprimées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="ffa5b-193">Vous ne remarquerez que cette modification car vous trouverez moins d’erreurs de compilateur pour les surcharges de méthode ambiguës si vous savez quelle méthode est la meilleure.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="ffa5b-194">Nouvelles options du compilateur</span><span class="sxs-lookup"><span data-stu-id="ffa5b-194">New compiler options</span></span>

<span data-ttu-id="ffa5b-195">De nouvelles options du compilateur prennent en charge la nouvelle build et les scénarios DevOps pour les programmes C#.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="ffa5b-196">Signature publique ou Open Source</span><span class="sxs-lookup"><span data-stu-id="ffa5b-196">Public or Open Source signing</span></span>

<span data-ttu-id="ffa5b-197">L’option du compilateur `-publicsign` indique au compilateur de signer l’assembly à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="ffa5b-198">L’assembly est marqué comme étant signé, mais la signature provient de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="ffa5b-199">Cette option vous permet de générer des assemblys signés à partir de projets open source à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="ffa5b-200">Pour plus d’informations, consultez l’article [Option du compilateur -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="ffa5b-201">pathmap</span><span class="sxs-lookup"><span data-stu-id="ffa5b-201">pathmap</span></span>

<span data-ttu-id="ffa5b-202">L’option du compilateur `-pathmap` indique au compilateur de remplacer les chemins sources de l’environnement de build par des chemins sources mappés.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="ffa5b-203">L’option `-pathmap` contrôle le chemin source écrit par le compilateur vers les fichiers PDB ou pour <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="ffa5b-204">Pour plus d’informations, consultez l’article [Option du compilateur -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ffa5b-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
