---
title: Nouveautés de C# 7.3
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: aca5c1b82253c02eccf24af1e5c45d0203d0b1b8
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832707"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="545c0-103">Nouveautés de C# 7.3</span><span class="sxs-lookup"><span data-stu-id="545c0-103">What's new in C# 7.3</span></span>

<span data-ttu-id="545c0-104">Il existe deux thèmes principaux pour la version C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="545c0-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="545c0-105">Un thème fournit des fonctionnalités permettant au code sécurisé d’être aussi performant que le code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="545c0-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="545c0-106">Le second thème fournit des améliorations incrémentielles aux fonctionnalités existantes.</span><span class="sxs-lookup"><span data-stu-id="545c0-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="545c0-107">En outre, de nouvelles options de compilateur ont été ajoutées à cette version.</span><span class="sxs-lookup"><span data-stu-id="545c0-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="545c0-108">Les nouvelles fonctionnalités suivantes prennent en charge le thème de meilleures performances pour le code sécurisé :</span><span class="sxs-lookup"><span data-stu-id="545c0-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="545c0-109">Vous pouvez accéder à des champs fixes sans épinglage.</span><span class="sxs-lookup"><span data-stu-id="545c0-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="545c0-110">Vous pouvez réaffecter des variables locales `ref`.</span><span class="sxs-lookup"><span data-stu-id="545c0-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="545c0-111">Vous pouvez utiliser des initialiseurs sur les tableaux `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="545c0-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="545c0-112">Vous pouvez utiliser des instructions `fixed` avec tout type prenant en charge un modèle.</span><span class="sxs-lookup"><span data-stu-id="545c0-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="545c0-113">Vous pouvez utiliser des contraintes génériques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="545c0-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="545c0-114">Les améliorations suivantes ont été apportées aux fonctionnalités existantes :</span><span class="sxs-lookup"><span data-stu-id="545c0-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="545c0-115">Vous pouvez tester `==` et `!=` avec des types de tuple.</span><span class="sxs-lookup"><span data-stu-id="545c0-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="545c0-116">Vous pouvez utiliser des variables d’expression dans d’autres emplacements.</span><span class="sxs-lookup"><span data-stu-id="545c0-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="545c0-117">Vous pouvez joindre des attributs à un champ de stockage de propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="545c0-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="545c0-118">La résolution de la méthode lorsque des arguments diffèrent de `in` a été améliorée.</span><span class="sxs-lookup"><span data-stu-id="545c0-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="545c0-119">La résolution de la surcharge comporte maintenant moins de cas ambigus.</span><span class="sxs-lookup"><span data-stu-id="545c0-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="545c0-120">Les nouvelles options du compilateur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="545c0-120">The new compiler options are:</span></span>

- <span data-ttu-id="545c0-121">`-publicsign` pour activer la signature d’assemblys Open Source Software (OSS).</span><span class="sxs-lookup"><span data-stu-id="545c0-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="545c0-122">`-pathmap` pour fournir un mappage des répertoires sources.</span><span class="sxs-lookup"><span data-stu-id="545c0-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="545c0-123">Le reste de cet article fournit des détails et des liens pour en savoir plus sur chacune de ces améliorations.</span><span class="sxs-lookup"><span data-stu-id="545c0-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="545c0-124">Code sécurisé plus performant</span><span class="sxs-lookup"><span data-stu-id="545c0-124">Enabling more efficient safe code</span></span>

<span data-ttu-id="545c0-125">Vous devez être en mesure d’écrire en toute sécurité un code C# ainsi performant qu’un code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="545c0-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="545c0-126">Le code sécurisé évite les classes d’erreurs, par exemple les dépassements de mémoire tampon, les pointeurs perdus et d’autres erreurs d’accès à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="545c0-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="545c0-127">Ces nouvelles fonctionnalités étendent les fonctionnalités de code sécurisé vérifiables.</span><span class="sxs-lookup"><span data-stu-id="545c0-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="545c0-128">Efforcez-vous d’utiliser plus de constructions sécurisées pour écrire votre code.</span><span class="sxs-lookup"><span data-stu-id="545c0-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="545c0-129">Ces fonctionnalités facilitent cette écriture.</span><span class="sxs-lookup"><span data-stu-id="545c0-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="545c0-130">L’indexation des champs `fixed` ne nécessite aucun épinglage</span><span class="sxs-lookup"><span data-stu-id="545c0-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="545c0-131">Prenons le struct suivant :</span><span class="sxs-lookup"><span data-stu-id="545c0-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="545c0-132">Dans les versions antérieures de C#, vous deviez épingler une variable pour accéder à un des entiers faisant partie de `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="545c0-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="545c0-133">À présent, le code suivant se compile sans épingler la variable `p` à l’intérieur d’une instruction `fixed` distincte :</span><span class="sxs-lookup"><span data-stu-id="545c0-133">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="545c0-134">La variable `p` accède à un élément dans `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="545c0-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="545c0-135">Vous n’avez pas besoin de déclarer une variable `int*` distincte.</span><span class="sxs-lookup"><span data-stu-id="545c0-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="545c0-136">Notez que vous avez toujours besoin d’un contexte `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="545c0-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="545c0-137">Dans les versions antérieures de C#, vous devez déclarer un second pointeur fixe :</span><span class="sxs-lookup"><span data-stu-id="545c0-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="545c0-138">Pour plus d’informations, consultez l’article sur [l’instruction `fixed`](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-138">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="545c0-139">Les variables locales `ref` peuvent être réaffectées</span><span class="sxs-lookup"><span data-stu-id="545c0-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="545c0-140">Désormais, les variables locales `ref` peuvent être réassignées pour faire référence à d’autres instances, après avoir été initialisées.</span><span class="sxs-lookup"><span data-stu-id="545c0-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="545c0-141">Le code suivant effectue maintenant une compilation :</span><span class="sxs-lookup"><span data-stu-id="545c0-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="545c0-142">Pour plus d’informations, consultez l’article sur les [retours `ref` et les variables locales `ref`](../programming-guide/classes-and-structs/ref-returns.md), et l’article sur [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="545c0-143">Les tableaux `stackalloc` prennent en charge les initialiseurs</span><span class="sxs-lookup"><span data-stu-id="545c0-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="545c0-144">Vous avez été en mesure de spécifier les valeurs des éléments dans un tableau lors de son initialisation :</span><span class="sxs-lookup"><span data-stu-id="545c0-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="545c0-145">Maintenant, la même syntaxe peut être appliquée aux tableaux déclarés avec `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="545c0-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="545c0-146">Pour plus d’informations, consultez l’article sur l’[opérateur `stackalloc`](../language-reference/operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-146">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="545c0-147">D’autres types prennent en charge l’instruction `fixed`</span><span class="sxs-lookup"><span data-stu-id="545c0-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="545c0-148">L’instruction `fixed` prenait en charge un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="545c0-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="545c0-149">À partir de C# 7.3, tout type contenant une méthode `GetPinnableReference()` qui retourne `ref T` ou `ref readonly T` peut être `fixed`.</span><span class="sxs-lookup"><span data-stu-id="545c0-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="545c0-150">L’ajout de cette fonctionnalité signifie que `fixed` peut être utilisé avec <xref:System.Span%601?displayProperty=nameWithType> et des types connexes.</span><span class="sxs-lookup"><span data-stu-id="545c0-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="545c0-151">Pour plus d’informations, consultez l’article [Instruction `fixed`](../language-reference/keywords/fixed-statement.md) dans la référence sur le langage.</span><span class="sxs-lookup"><span data-stu-id="545c0-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="545c0-152">Contraintes génériques améliorées</span><span class="sxs-lookup"><span data-stu-id="545c0-152">Enhanced generic constraints</span></span>

<span data-ttu-id="545c0-153">Vous pouvez maintenant spécifier le type <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> en tant que contraintes de classe de base pour un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="545c0-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="545c0-154">Vous pouvez également utiliser la nouvelle contrainte `unmanaged` pour spécifier qu’un paramètre de type doit être un **type non managé**.</span><span class="sxs-lookup"><span data-stu-id="545c0-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="545c0-155">Un **type non managé** est un type qui n’est pas un type référence et ne contient pas de type référence à tous les niveaux d’imbrication.</span><span class="sxs-lookup"><span data-stu-id="545c0-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="545c0-156">Pour plus d’informations, consultez les articles sur les [contraintes génériques `where`](../language-reference/keywords/where-generic-type-constraint.md) et les [contraintes sur les paramètres de type](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="545c0-157">L’ajout de ces contraintes aux types existants est une [modification incompatible](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="545c0-157">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="545c0-158">Les types génériques fermés peuvent ne plus respecter ces nouvelles contraintes.</span><span class="sxs-lookup"><span data-stu-id="545c0-158">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="545c0-159">Améliorer les fonctionnalités existantes</span><span class="sxs-lookup"><span data-stu-id="545c0-159">Make existing features better</span></span>

<span data-ttu-id="545c0-160">Le second thème fournit des améliorations apportées aux fonctionnalités du langage.</span><span class="sxs-lookup"><span data-stu-id="545c0-160">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="545c0-161">Ces fonctionnalités améliorent la productivité lors de l’écriture de code C#.</span><span class="sxs-lookup"><span data-stu-id="545c0-161">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="545c0-162">Les tuples prennent en charge `==` et `!=`</span><span class="sxs-lookup"><span data-stu-id="545c0-162">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="545c0-163">Les types tuple C# prennent désormais en charge `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="545c0-163">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="545c0-164">Pour plus d’informations, consultez la section consacrée à [l’égalité](../tuples.md#equality-and-tuples) dans l’article sur les [tuples](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-164">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="545c0-165">Joindre des attributs à des champs de stockage pour les propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="545c0-165">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="545c0-166">Cette syntaxe est maintenant prise en charge :</span><span class="sxs-lookup"><span data-stu-id="545c0-166">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="545c0-167">L’attribut `SomeThingAboutFieldAttribute` est appliqué au champ de stockage généré par le compilateur pour `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="545c0-167">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="545c0-168">Pour plus d’informations, consultez les [attributs](../programming-guide/concepts/attributes/index.md) dans le guide de programmation C#.</span><span class="sxs-lookup"><span data-stu-id="545c0-168">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="545c0-169">`in` critère de résolution de surcharge de méthode</span><span class="sxs-lookup"><span data-stu-id="545c0-169">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="545c0-170">Lorsque le modificateur de l’argument `in` a été ajouté, ces deux méthodes provoqueraient une ambiguïté :</span><span class="sxs-lookup"><span data-stu-id="545c0-170">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="545c0-171">À présent, la surcharge par valeur (la première dans l’exemple précédent) est meilleure que la version de référence en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="545c0-171">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="545c0-172">Pour appeler la version avec l’argument de référence en lecture seule, vous devez inclure le modificateur `in` lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="545c0-172">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="545c0-173">Cette opération a été implémentée en tant que correctif de bogue.</span><span class="sxs-lookup"><span data-stu-id="545c0-173">This was implemented as a bug fix.</span></span> <span data-ttu-id="545c0-174">Il n’y a donc plus d’ambiguïté, même si la version du langage est définie sur « 7.2 ».</span><span class="sxs-lookup"><span data-stu-id="545c0-174">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="545c0-175">Pour plus d’informations, consultez l’article sur le [modificateur de paramètre `in`](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-175">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="545c0-176">Étendre des variables d’expression dans les initialiseurs</span><span class="sxs-lookup"><span data-stu-id="545c0-176">Extend expression variables in initializers</span></span>

<span data-ttu-id="545c0-177">La syntaxe ajoutée dans C# 7.0 pour autoriser les déclarations variables `out` a été étendue pour inclure des initialiseurs de champ, des initialiseurs de propriété, des initialiseurs de constructeur et des clauses de requête.</span><span class="sxs-lookup"><span data-stu-id="545c0-177">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="545c0-178">Il permet d’écrire un code tel que l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="545c0-178">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="545c0-179">Candidats de surcharge améliorés</span><span class="sxs-lookup"><span data-stu-id="545c0-179">Improved overload candidates</span></span>

<span data-ttu-id="545c0-180">Dans chaque version, les règles de résolution de surcharge ont été mises à jour pour résoudre les situations où des appels de méthode ambigus sont face à un choix « évident ».</span><span class="sxs-lookup"><span data-stu-id="545c0-180">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="545c0-181">Cette version ajoute trois nouvelles règles pour aider le compilateur à opter pour le choix évident :</span><span class="sxs-lookup"><span data-stu-id="545c0-181">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="545c0-182">Lorsqu’un groupe de méthodes contient à la fois une instance et des membres statiques, le compilateur ignore les membres de l’instance si la méthode a été appelée sans récepteur d’instance ou contexte.</span><span class="sxs-lookup"><span data-stu-id="545c0-182">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="545c0-183">Le compilateur ignore les membres statiques si la méthode a été appelée avec un récepteur d’instance.</span><span class="sxs-lookup"><span data-stu-id="545c0-183">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="545c0-184">Lorsqu’il n’existe aucun récepteur, le compilateur inclut uniquement les membres statiques dans un contexte statique, sinon, à la fois les membres statiques et les membres de l’instance.</span><span class="sxs-lookup"><span data-stu-id="545c0-184">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="545c0-185">Lorsque le récepteur représente de façon ambiguë une instance ou un type, le compilateur inclut les deux éléments.</span><span class="sxs-lookup"><span data-stu-id="545c0-185">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="545c0-186">Un contexte statique, où un récepteur d’instance `this` implicite ne peut pas être utilisé, inclut le corps des membres où aucun `this` n’est défini, par exemple des membres statiques, ainsi que chaque endroit où `this` ne peut pas être utilisé, par exemple les initialiseurs de champ et les initialiseurs de constructeur.</span><span class="sxs-lookup"><span data-stu-id="545c0-186">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="545c0-187">Lorsqu’un groupe de méthodes contient certaines méthodes génériques dont les arguments de type ne répondent pas à leurs contraintes, ces membres sont supprimés de l’ensemble de candidats.</span><span class="sxs-lookup"><span data-stu-id="545c0-187">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="545c0-188">Pour une conversion de groupe de méthodes, les méthodes candidates dont le type de retour ne correspond pas à celui du délégué sont supprimées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="545c0-188">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="545c0-189">Vous ne remarquerez que cette modification car vous trouverez moins d’erreurs de compilateur pour les surcharges de méthode ambiguës si vous savez quelle méthode est la meilleure.</span><span class="sxs-lookup"><span data-stu-id="545c0-189">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="545c0-190">Nouvelles options du compilateur</span><span class="sxs-lookup"><span data-stu-id="545c0-190">New compiler options</span></span>

<span data-ttu-id="545c0-191">De nouvelles options du compilateur prennent en charge la nouvelle build et les scénarios DevOps pour les programmes C#.</span><span class="sxs-lookup"><span data-stu-id="545c0-191">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="545c0-192">Signature publique ou Open Source</span><span class="sxs-lookup"><span data-stu-id="545c0-192">Public or Open Source signing</span></span>

<span data-ttu-id="545c0-193">L’option du compilateur `-publicsign` indique au compilateur de signer l’assembly à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="545c0-193">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="545c0-194">L’assembly est marqué comme étant signé, mais la signature provient de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="545c0-194">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="545c0-195">Cette option vous permet de générer des assemblys signés à partir de projets open source à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="545c0-195">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="545c0-196">Pour plus d’informations, consultez l’article [Option du compilateur -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-196">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="545c0-197">pathmap</span><span class="sxs-lookup"><span data-stu-id="545c0-197">pathmap</span></span>

<span data-ttu-id="545c0-198">L’option du compilateur `-pathmap` indique au compilateur de remplacer les chemins sources de l’environnement de build par des chemins sources mappés.</span><span class="sxs-lookup"><span data-stu-id="545c0-198">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="545c0-199">L’option `-pathmap` contrôle le chemin source écrit par le compilateur vers les fichiers PDB ou pour <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="545c0-199">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="545c0-200">Pour plus d’informations, consultez l’article [Option du compilateur -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="545c0-200">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
