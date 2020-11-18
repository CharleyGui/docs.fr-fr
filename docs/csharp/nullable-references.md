---
title: Types références Nullables
description: Cet article fournit une vue d’ensemble des types de référence Nullable, ajoutés en C# 8,0. Vous allez découvrir comment la fonctionnalité offre une protection contre les exceptions de référence null pour les projets nouveaux ou existants.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 8a86546ef4adfd7695d957f807a62972b00316dc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829165"
---
# <a name="nullable-reference-types"></a><span data-ttu-id="95f4b-104">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="95f4b-104">Nullable reference types</span></span>

<span data-ttu-id="95f4b-105">C# 8.0 introduit des **types référence nullables** et des **types référence non nullables** qui vous permettent d’établir des instructions importantes sur les propriétés de variables de type référence :</span><span class="sxs-lookup"><span data-stu-id="95f4b-105">C# 8.0 introduces **nullable reference types** and **non-nullable reference types** that enable you to make important statements about the properties for reference type variables:</span></span>

- <span data-ttu-id="95f4b-106">**Une référence ne doit pas être null**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-106">**A reference isn't supposed to be null**.</span></span> <span data-ttu-id="95f4b-107">Lorsque les variables ne sont pas censées être null, le compilateur applique des règles qui garantissent que le déréférencement de ces variables est sécurisé sans avoir d’abord vérifié qu’elle n’est pas NULL :</span><span class="sxs-lookup"><span data-stu-id="95f4b-107">When variables aren't supposed to be null, the compiler enforces rules that ensure it's safe to dereference these variables without first checking that it isn't null:</span></span>
  - <span data-ttu-id="95f4b-108">La variable doit être initialisée avec une valeur non null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-108">The variable must be initialized to a non-null value.</span></span>
  - <span data-ttu-id="95f4b-109">La variable ne peut jamais se voir attribuer la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="95f4b-109">The variable can never be assigned the value `null`.</span></span>
- <span data-ttu-id="95f4b-110">**Une référence peut être null**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-110">**A reference may be null**.</span></span> <span data-ttu-id="95f4b-111">Lorsque les variables peuvent être null, le compilateur applique des règles différentes pour garantir que vous avez correctement vérifié une référence null :</span><span class="sxs-lookup"><span data-stu-id="95f4b-111">When variables may be null, the compiler enforces different rules to ensure that you've correctly checked for a null reference:</span></span>
  - <span data-ttu-id="95f4b-112">La variable peut être déréférencée seulement si le compilateur peut garantir que la valeur n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-112">The variable may only be dereferenced when the compiler can guarantee that the value isn't null.</span></span>
  - <span data-ttu-id="95f4b-113">Ces variables peuvent être initialisées avec la valeur `null` par défaut et peuvent se voir attribuer la valeur `null` dans un autre code.</span><span class="sxs-lookup"><span data-stu-id="95f4b-113">These variables may be initialized with the default `null` value and may be assigned the value `null` in other code.</span></span>

<span data-ttu-id="95f4b-114">Cette nouvelle fonctionnalité offre des avantages significatifs par rapport à la gestion des variables de référence dans les versions antérieures de C#, où l’intention de conception ne peut pas être déterminée à partir de la déclaration de la variable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-114">This new feature provides significant benefits over the handling of reference variables in earlier versions of C# where the design intent can't be determined from the variable declaration.</span></span> <span data-ttu-id="95f4b-115">Le compilateur ne protégeait pas des exceptions de référence null pour les types référence :</span><span class="sxs-lookup"><span data-stu-id="95f4b-115">The compiler didn't provide safety against null reference exceptions for reference types:</span></span>

- <span data-ttu-id="95f4b-116">**Une référence peut être null**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-116">**A reference can be null**.</span></span> <span data-ttu-id="95f4b-117">Le compilateur n’émet pas d’avertissements quand une variable de type référence est initialisée à `null` ou ultérieurement assignée `null` .</span><span class="sxs-lookup"><span data-stu-id="95f4b-117">The compiler doesn't issue warnings when a reference-type variable is initialized to `null`, or later assigned `null`.</span></span> <span data-ttu-id="95f4b-118">Le compilateur émet des avertissements lorsque ces variables sont déréférencées sans contrôles null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-118">The compiler issues warnings when these variables are dereferenced without null checks.</span></span>
- <span data-ttu-id="95f4b-119">**Une référence est censée ne pas être null**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-119">**A reference is assumed to be not null**.</span></span> <span data-ttu-id="95f4b-120">Le compilateur ne génère aucun avertissement quand les types référence sont déréférencés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-120">The compiler doesn't issue any warnings when reference types are dereferenced.</span></span> <span data-ttu-id="95f4b-121">Le compilateur émet des avertissements si une variable est définie sur une expression qui peut être null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-121">The compiler issues warnings if a variable is set to an expression that may be null.</span></span>

<span data-ttu-id="95f4b-122">Ces avertissements sont émis au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="95f4b-122">These warnings are emitted at compile time.</span></span> <span data-ttu-id="95f4b-123">Le compilateur n’ajoute pas de contrôles null ou autres constructions d’exécution dans un contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-123">The compiler doesn't add any null checks or other runtime constructs in a nullable context.</span></span> <span data-ttu-id="95f4b-124">Au moment de l’exécution, une référence Nullable et une référence non Nullable sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="95f4b-124">At runtime, a nullable reference and a non-nullable reference are equivalent.</span></span>

<span data-ttu-id="95f4b-125">En ajoutant des types référence nullables, vous pouvez déclarer votre intention plus clairement.</span><span class="sxs-lookup"><span data-stu-id="95f4b-125">With the addition of nullable reference types, you can declare your intent more clearly.</span></span> <span data-ttu-id="95f4b-126">La valeur `null` est un bon moyen de représenter qu’une variable ne fait pas référence à une valeur.</span><span class="sxs-lookup"><span data-stu-id="95f4b-126">The `null` value is the correct way to represent that a variable doesn't refer to a value.</span></span> <span data-ttu-id="95f4b-127">N’utilisez pas cette fonctionnalité pour supprimer toutes les valeurs `null` de votre code.</span><span class="sxs-lookup"><span data-stu-id="95f4b-127">Don't use this feature to remove all `null` values from your code.</span></span> <span data-ttu-id="95f4b-128">Déclarez plutôt votre intention au compilateur et aux autres développeurs qui lisent votre code.</span><span class="sxs-lookup"><span data-stu-id="95f4b-128">Rather, you should declare your intent to the compiler and other developers that read your code.</span></span> <span data-ttu-id="95f4b-129">Quand vous déclarez votre intention, le compilateur vous informe si vous écrivez du code qui n’est pas en phase avec cette intention.</span><span class="sxs-lookup"><span data-stu-id="95f4b-129">By declaring your intent, the compiler informs you when you write code that is inconsistent with that intent.</span></span>

<span data-ttu-id="95f4b-130">Un **type de référence nullable** est inidqué avec la même syntaxe que celle des [types valeur nullable](language-reference/builtin-types/nullable-value-types.md) : un `?` est ajouté au type de la variable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-130">A **nullable reference type** is noted using the same syntax as [nullable value types](language-reference/builtin-types/nullable-value-types.md): a `?` is appended to the type of the variable.</span></span> <span data-ttu-id="95f4b-131">Par exemple, la déclaration de variable suivante représente une variable de chaîne nullable, `name` :</span><span class="sxs-lookup"><span data-stu-id="95f4b-131">For example, the following variable declaration represents a nullable string variable, `name`:</span></span>

```csharp
string? name;
```

<span data-ttu-id="95f4b-132">Toute variable où `?` n’est pas ajouté au nom de type est un **type de référence non Nullable**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-132">Any variable where the `?` isn't appended to the type name is a **non-nullable reference type**.</span></span> <span data-ttu-id="95f4b-133">Cela comprend toutes les variables de type référence dans le code existant lorsque vous avez activé cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="95f4b-133">That includes all reference type variables in existing code when you've enabled this feature.</span></span>

<span data-ttu-id="95f4b-134">Le compilateur utilise l’analyse statique pour déterminer si une référence nullable est connue pour être non null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-134">The compiler uses static analysis to determine if a nullable reference is known to be non-null.</span></span> <span data-ttu-id="95f4b-135">Le compilateur vous avertit si vous déréférencez une référence nullable quand elle est susceptible d’être null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-135">The compiler warns you if you dereference a nullable reference when it may be null.</span></span> <span data-ttu-id="95f4b-136">Vous pouvez remplacer ce comportement à l’aide de l' [opérateur null-indulgent avec](language-reference/operators/null-forgiving.md) à la `!` suite d’un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-136">You can override this behavior by using the [null-forgiving operator](language-reference/operators/null-forgiving.md) `!` following a variable name.</span></span> <span data-ttu-id="95f4b-137">Par exemple, si vous savez que la variable `name` n’est pas null alors que le compilateur génère un avertissement, vous pouvez écrire le code suivant pour remplacer l’analyse du compilateur :</span><span class="sxs-lookup"><span data-stu-id="95f4b-137">For example, if you know the `name` variable isn't null but the compiler issues a warning, you can write the following code to override the compiler's analysis:</span></span>

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a><span data-ttu-id="95f4b-138">Nullabilité des types</span><span class="sxs-lookup"><span data-stu-id="95f4b-138">Nullability of types</span></span>

<span data-ttu-id="95f4b-139">Tout type référence peut avoir l’une des quatre *nullabilités*, qui décrit quand des avertissements sont générés :</span><span class="sxs-lookup"><span data-stu-id="95f4b-139">Any reference type can have one of four *nullabilities*, which describes when warnings are generated:</span></span>

- <span data-ttu-id="95f4b-140">Non *null*: aucune valeur NULL ne peut être assignée aux variables de ce type.</span><span class="sxs-lookup"><span data-stu-id="95f4b-140">*Nonnullable*: Null can't be assigned to variables of this type.</span></span> <span data-ttu-id="95f4b-141">Les variables de ce type n’ont pas besoin d’être vérifiées pour savoir si elles ont la valeur null avant d’être déréférencées.</span><span class="sxs-lookup"><span data-stu-id="95f4b-141">Variables of this type don't need to be null-checked before dereferencing.</span></span>
- <span data-ttu-id="95f4b-142">*Nullable*: la valeur NULL peut être assignée aux variables de ce type.</span><span class="sxs-lookup"><span data-stu-id="95f4b-142">*Nullable*: Null can be assigned to variables of this type.</span></span> <span data-ttu-id="95f4b-143">Le déréférencement des variables de ce type sans vérifier `null` au préalable génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="95f4b-143">Dereferencing variables of this type without first checking for `null` causes a warning.</span></span>
- <span data-ttu-id="95f4b-144">*Oublie*: oublie est l’état pré-C # 8,0.</span><span class="sxs-lookup"><span data-stu-id="95f4b-144">*Oblivious*: Oblivious is the pre-C# 8.0 state.</span></span> <span data-ttu-id="95f4b-145">Les variables de ce type peuvent être déréférencées ou attribuées sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="95f4b-145">Variables of this type can be dereferenced or assigned without warnings.</span></span>
- <span data-ttu-id="95f4b-146">*Inconnu*: inconnu est généralement utilisé pour les paramètres de type où les contraintes n’indiquent pas au compilateur que le type doit être *Nullable* ou ne peut pas être *null*.</span><span class="sxs-lookup"><span data-stu-id="95f4b-146">*Unknown*: Unknown is generally for type parameters where constraints don't tell the compiler that the type must be *nullable* or *nonnullable*.</span></span>

<span data-ttu-id="95f4b-147">La nullabilité d’un type dans une déclaration de variable est contrôlée par le *contexte nullable* dans lequel la variable est déclarée.</span><span class="sxs-lookup"><span data-stu-id="95f4b-147">The nullability of a type in a variable declaration is controlled by the *nullable context* in which the variable is declared.</span></span>

## <a name="nullable-contexts"></a><span data-ttu-id="95f4b-148">Contextes nullables</span><span class="sxs-lookup"><span data-stu-id="95f4b-148">Nullable contexts</span></span>

<span data-ttu-id="95f4b-149">Les contextes nullables permettent de contrôler précisément comment le compilateur interprète les variables de type référence.</span><span class="sxs-lookup"><span data-stu-id="95f4b-149">Nullable contexts enable fine-grained control for how the compiler interprets reference type variables.</span></span> <span data-ttu-id="95f4b-150">Le **contexte d’annotation Nullable** d’une ligne source donnée est activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="95f4b-150">The **nullable annotation context** of any given source line is either enabled or disabled.</span></span> <span data-ttu-id="95f4b-151">Vous pouvez considérer le compilateur pre-C # 8,0 comme en compilant tout votre code dans un contexte Nullable désactivé : tout type de référence peut être null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-151">You can think of the pre-C# 8.0 compiler as compiling all your code in a disabled nullable context: any reference type may be null.</span></span> <span data-ttu-id="95f4b-152">Le **contexte d’avertissements Nullable** peut également être activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="95f4b-152">The **nullable warnings context** may also be enabled or disabled.</span></span> <span data-ttu-id="95f4b-153">Le contexte d’avertissements nullable spécifie les avertissements générés par le compilateur à l’aide de son analyse de flux.</span><span class="sxs-lookup"><span data-stu-id="95f4b-153">The nullable warnings context specifies the warnings generated by the compiler using its flow analysis.</span></span>

<span data-ttu-id="95f4b-154">Le contexte d’annotation Nullable et le contexte d’avertissement Nullable peuvent être définis pour un projet à l’aide de l' `Nullable` élément dans votre fichier *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="95f4b-154">The nullable annotation context and nullable warning context can be set for a project using the `Nullable` element in your *.csproj* file.</span></span> <span data-ttu-id="95f4b-155">Cet élément configure comment le compilateur interprète la nullabilité des types et quels avertissements sont générés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-155">This element configures how the compiler interprets the nullability of types and what warnings are generated.</span></span> <span data-ttu-id="95f4b-156">Les paramètres valides sont :</span><span class="sxs-lookup"><span data-stu-id="95f4b-156">Valid settings are:</span></span>

- <span data-ttu-id="95f4b-157">`enable`: Le contexte d’annotation Nullable est **activé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-157">`enable`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="95f4b-158">Le contexte d’avertissement nullable est **activé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-158">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="95f4b-159">Les variables d’un type référence, `string` par exemple, sont non nullables.</span><span class="sxs-lookup"><span data-stu-id="95f4b-159">Variables of a reference type, `string` for example, are non-nullable.</span></span>  <span data-ttu-id="95f4b-160">Tous les avertissements de nullabilité sont activés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-160">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="95f4b-161">`warnings`: Le contexte d’annotation Nullable est **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-161">`warnings`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="95f4b-162">Le contexte d’avertissement nullable est **activé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-162">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="95f4b-163">Les variables d’un type référence sont oblivious.</span><span class="sxs-lookup"><span data-stu-id="95f4b-163">Variables of a reference type are oblivious.</span></span> <span data-ttu-id="95f4b-164">Tous les avertissements de nullabilité sont activés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-164">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="95f4b-165">`annotations`: Le contexte d’annotation Nullable est **activé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-165">`annotations`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="95f4b-166">Le contexte d’avertissement nullable est **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-166">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="95f4b-167">Les variables d’un type référence, String par exemple, ne sont pas nullables.</span><span class="sxs-lookup"><span data-stu-id="95f4b-167">Variables of a reference type, string for example, are non-nullable.</span></span> <span data-ttu-id="95f4b-168">Tous les avertissements de nullabilité sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-168">All nullability warnings are disabled.</span></span>
- <span data-ttu-id="95f4b-169">`disable`: Le contexte d’annotation Nullable est **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-169">`disable`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="95f4b-170">Le contexte d’avertissement nullable est **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-170">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="95f4b-171">Les variables d’un type référence sont oblivious, comme dans les versions antérieures de C#.</span><span class="sxs-lookup"><span data-stu-id="95f4b-171">Variables of a reference type are oblivious, just like earlier versions of C#.</span></span> <span data-ttu-id="95f4b-172">Tous les avertissements de nullabilité sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="95f4b-172">All nullability warnings are disabled.</span></span>

<span data-ttu-id="95f4b-173">**Exemple** :</span><span class="sxs-lookup"><span data-stu-id="95f4b-173">**Example**:</span></span>

```xml
<Nullable>enable</Nullable>
```

<span data-ttu-id="95f4b-174">Vous pouvez aussi utiliser des directives pour définir ces mêmes contextes partout dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="95f4b-174">You can also use directives to set these same contexts anywhere in your project:</span></span>

- <span data-ttu-id="95f4b-175">`#nullable enable`: Définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **activé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-175">`#nullable enable`: Sets the nullable annotation context and nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="95f4b-176">`#nullable disable`: Définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-176">`#nullable disable`: Sets the nullable annotation context and nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="95f4b-177">`#nullable restore`: Restaure le contexte d’annotation Nullable et le contexte d’avertissement Nullable aux paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="95f4b-177">`#nullable restore`: Restores the nullable annotation context and nullable warning context to the project settings.</span></span>
- <span data-ttu-id="95f4b-178">`#nullable disable warnings`: Affectez la valeur **désactivé** au contexte d’avertissement Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-178">`#nullable disable warnings`: Set the nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="95f4b-179">`#nullable enable warnings`: Affectez la valeur **activé** au contexte d’avertissement Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-179">`#nullable enable warnings`: Set the nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="95f4b-180">`#nullable restore warnings`: Restaure le contexte d’avertissement Nullable aux paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="95f4b-180">`#nullable restore warnings`: Restores the nullable warning context to the project settings.</span></span>
- <span data-ttu-id="95f4b-181">`#nullable disable annotations`: Affectez la valeur **désactivé** au contexte d’annotation Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-181">`#nullable disable annotations`: Set the nullable annotation context to **disabled**.</span></span>
- <span data-ttu-id="95f4b-182">`#nullable enable annotations`: Affectez la valeur **activé** au contexte d’annotation Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-182">`#nullable enable annotations`: Set the nullable annotation context to **enabled**.</span></span>
- <span data-ttu-id="95f4b-183">`#nullable restore annotations`: Restaure le contexte d’avertissement d’annotation aux paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="95f4b-183">`#nullable restore annotations`: Restores the annotation warning context to the project settings.</span></span>

<span data-ttu-id="95f4b-184">Par défaut, l’annotation Nullable et les contextes d’avertissement sont **désactivés**, y compris les nouveaux projets.</span><span class="sxs-lookup"><span data-stu-id="95f4b-184">By default, nullable annotation and warning contexts are **disabled**, including new projects.</span></span> <span data-ttu-id="95f4b-185">Cela signifie que votre code existant est compilé sans modification et sans générer de nouveaux avertissements.</span><span class="sxs-lookup"><span data-stu-id="95f4b-185">That means that your existing code compiles without changes and without generating any new warnings.</span></span>

<span data-ttu-id="95f4b-186">Ces options fournissent deux stratégies distinctes pour [mettre à jour une base de code existante](nullable-migration-strategies.md) afin d’utiliser des types de référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-186">These options provide two distinct strategies to [update an existing codebase](nullable-migration-strategies.md) to use nullable reference types.</span></span>

## <a name="nullable-annotation-context"></a><span data-ttu-id="95f4b-187">Contexte d’annotation nullable</span><span class="sxs-lookup"><span data-stu-id="95f4b-187">Nullable annotation context</span></span>

<span data-ttu-id="95f4b-188">Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable désactivé :</span><span class="sxs-lookup"><span data-stu-id="95f4b-188">The compiler uses the following rules in a disabled nullable annotation context:</span></span>

- <span data-ttu-id="95f4b-189">Vous ne pouvez pas déclarer de références nullables dans un contexte désactivé.</span><span class="sxs-lookup"><span data-stu-id="95f4b-189">You can't declare nullable references in a disabled context.</span></span>
- <span data-ttu-id="95f4b-190">Une valeur NULL peut être assignée à toutes les variables de référence.</span><span class="sxs-lookup"><span data-stu-id="95f4b-190">All reference variables may be assigned a value of null.</span></span>
- <span data-ttu-id="95f4b-191">Aucun avertissement n’est généré lorsqu’une variable d’un type référence est déréférencée.</span><span class="sxs-lookup"><span data-stu-id="95f4b-191">No warnings are generated when a variable of a reference type is dereferenced.</span></span>
- <span data-ttu-id="95f4b-192">L’opérateur null-forgiving ne peut pas être utilisé dans un contexte désactivé.</span><span class="sxs-lookup"><span data-stu-id="95f4b-192">The null-forgiving operator may not be used in a disabled context.</span></span>

<span data-ttu-id="95f4b-193">Le comportement est le même que dans les versions précédentes de C#.</span><span class="sxs-lookup"><span data-stu-id="95f4b-193">The behavior is the same as previous versions of C#.</span></span>

<span data-ttu-id="95f4b-194">Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable activé :</span><span class="sxs-lookup"><span data-stu-id="95f4b-194">The compiler uses the following rules in an enabled nullable annotation context:</span></span>

- <span data-ttu-id="95f4b-195">Toute variable d’un type référence est une **référence non nullable**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-195">Any variable of a reference type is a **non-nullable reference**.</span></span>
- <span data-ttu-id="95f4b-196">Toute référence non nullable peut être déréférencée sans problème.</span><span class="sxs-lookup"><span data-stu-id="95f4b-196">Any non-nullable reference may be dereferenced safely.</span></span>
- <span data-ttu-id="95f4b-197">Tout type référence nullable (indiqué par `?` après le type dans la déclaration de variable) peut être null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-197">Any nullable reference type (noted by `?` after the type in the variable declaration) may be null.</span></span> <span data-ttu-id="95f4b-198">L’analyse statique détermine si la valeur est connue pour être non null lorsqu’elle est déréférencée.</span><span class="sxs-lookup"><span data-stu-id="95f4b-198">Static analysis determines if the value is known to be non-null when it's dereferenced.</span></span> <span data-ttu-id="95f4b-199">Si ce n’est pas le cas, le compilateur vous avertit.</span><span class="sxs-lookup"><span data-stu-id="95f4b-199">If not, the compiler warns you.</span></span>
- <span data-ttu-id="95f4b-200">Vous pouvez utiliser l’opérateur null-forgiving pour déclarer qu’une référence nullable n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-200">You can use the null-forgiving operator to declare that a nullable reference isn't null.</span></span>

<span data-ttu-id="95f4b-201">Dans un contexte d’annotation nullable activé, le caractère `?` ajouté à un type référence déclare un **type référence nullable**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-201">In an enabled nullable annotation context, the `?` character appended to a reference type declares a **nullable reference type**.</span></span> <span data-ttu-id="95f4b-202">L' **opérateur null-indulgent avec** `!` peut être ajouté à une expression pour déclarer que l’expression n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-202">The **null-forgiving operator** `!` may be appended to an expression to declare that the expression isn't null.</span></span>

## <a name="nullable-warning-context"></a><span data-ttu-id="95f4b-203">Contexte d’avertissement nullable</span><span class="sxs-lookup"><span data-stu-id="95f4b-203">Nullable warning context</span></span>

<span data-ttu-id="95f4b-204">Le contexte d’avertissement nullable est différent du contexte d’annotation nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-204">The nullable warning context is distinct from the nullable annotation context.</span></span> <span data-ttu-id="95f4b-205">Des avertissements peuvent être activés, même lorsque les nouvelles annotations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="95f4b-205">Warnings can be enabled even when the new annotations are disabled.</span></span> <span data-ttu-id="95f4b-206">Le compilateur utilise l’analyse de flux statique pour déterminer l’**état null** de toutes les références.</span><span class="sxs-lookup"><span data-stu-id="95f4b-206">The compiler uses static flow analysis to determine the **null state** of any reference.</span></span> <span data-ttu-id="95f4b-207">L’état null est **non null** ou **peut-être null** quand le *contexte d’avertissement nullable* n’est pas **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="95f4b-207">The null state is either **not null** or **maybe null** when the *nullable warning context* isn't **disabled**.</span></span> <span data-ttu-id="95f4b-208">Si vous déréférencez une référence quand le compilateur a déterminé qu’elle est **peut-être null**, le compilateur vous avertit.</span><span class="sxs-lookup"><span data-stu-id="95f4b-208">If you dereference a reference when the compiler has determined it's **maybe null**, the compiler warns you.</span></span> <span data-ttu-id="95f4b-209">L’état d’une référence est **peut-être null**, sauf si le compilateur peut déterminer une des deux conditions :</span><span class="sxs-lookup"><span data-stu-id="95f4b-209">The state of a reference is **maybe null** unless the compiler can determine one of two conditions:</span></span>

1. <span data-ttu-id="95f4b-210">Une valeur non null a été assignée définitivement à la variable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-210">The variable has been definitely assigned a non-null value.</span></span>
1. <span data-ttu-id="95f4b-211">La variable ou l’expression a été vérifiée pour savoir si sa valeur est null avant de la référencer.</span><span class="sxs-lookup"><span data-stu-id="95f4b-211">The variable or expression has been checked against null before de-referencing it.</span></span>

<span data-ttu-id="95f4b-212">Le compilateur génère des avertissements lorsque vous déréférencez une variable ou une expression qui est **peut-être null** dans un contexte d’avertissement Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-212">The compiler generates warnings when you dereference a variable or expression that is **maybe null** in a nullable warning context.</span></span> <span data-ttu-id="95f4b-213">En outre, le compilateur génère des avertissements quand une variable de type référence non null reçoit une variable ou une expression de type **null** dans un contexte d’annotation Nullable activé.</span><span class="sxs-lookup"><span data-stu-id="95f4b-213">Furthermore, the compiler generates warnings when a nonnullable reference-type variable is assigned a **maybe null** variable or expression in an enabled nullable annotation context.</span></span>

## <a name="attributes-describe-apis"></a><span data-ttu-id="95f4b-214">Les attributs décrivent des API</span><span class="sxs-lookup"><span data-stu-id="95f4b-214">Attributes describe APIs</span></span>

<span data-ttu-id="95f4b-215">Vous ajoutez des attributs aux API qui fournissent au compilateur plus d’informations sur le moment où les arguments ou les valeurs de retour peuvent ou ne peuvent pas être null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-215">You add attributes to APIs that provide the compiler more information about when arguments or return values can or can't be null.</span></span> <span data-ttu-id="95f4b-216">Vous pouvez en savoir plus sur ces attributs dans notre article dans la référence du langage couvrant les [attributs Nullable](language-reference/attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="95f4b-216">You can learn more about these attributes in our article in the language reference covering the [nullable attributes](language-reference/attributes/nullable-analysis.md).</span></span> <span data-ttu-id="95f4b-217">Ces attributs sont ajoutés aux bibliothèques .NET sur les versions actuelles et à venir.</span><span class="sxs-lookup"><span data-stu-id="95f4b-217">These attributes are being added to .NET libraries over current and upcoming releases.</span></span> <span data-ttu-id="95f4b-218">Les API les plus couramment utilisées sont mises à jour en premier.</span><span class="sxs-lookup"><span data-stu-id="95f4b-218">The most commonly used APIs are being updated first.</span></span>

## <a name="known-pitfalls"></a><span data-ttu-id="95f4b-219">Pièges connus</span><span class="sxs-lookup"><span data-stu-id="95f4b-219">Known pitfalls</span></span>

<span data-ttu-id="95f4b-220">Les tableaux et les structs qui contiennent des types référence sont des pièges connus dans la fonctionnalité de types référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-220">Arrays and structs that contain reference types are known pitfalls in nullable reference types feature.</span></span>

### <a name="structs"></a><span data-ttu-id="95f4b-221">Structures</span><span class="sxs-lookup"><span data-stu-id="95f4b-221">Structs</span></span>

<span data-ttu-id="95f4b-222">Un struct qui contient des types référence n’acceptant pas les valeurs NULL permet de l’assigner `default` sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="95f4b-222">A struct that contains non-nullable reference types allows assigning `default` for it without any warnings.</span></span> <span data-ttu-id="95f4b-223">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="95f4b-223">Consider the following example:</span></span>

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

<span data-ttu-id="95f4b-224">Dans l’exemple précédent, il n’y a pas d’avertissement dans `PrintStudent(default)` tandis que les types de référence non Nullable `FirstName` et `LastName` sont null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-224">In the preceding example, there is no warning in `PrintStudent(default)` while the non-nullable reference types `FirstName` and `LastName` are null.</span></span>

<span data-ttu-id="95f4b-225">Un autre cas plus courant est lorsque vous traitez des structs génériques.</span><span class="sxs-lookup"><span data-stu-id="95f4b-225">Another more common case is when you deal with generic structs.</span></span> <span data-ttu-id="95f4b-226">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="95f4b-226">Consider the following example:</span></span>

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

<span data-ttu-id="95f4b-227">Dans l’exemple précédent, la propriété `Bar` va être `null` au moment de l’exécution et elle est assignée à une chaîne non Nullable sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="95f4b-227">In the preceding example, the property `Bar` is going to be `null` at runtime, and it's assigned to non-nullable string without any warnings.</span></span>

### <a name="arrays"></a><span data-ttu-id="95f4b-228">Tableaux</span><span class="sxs-lookup"><span data-stu-id="95f4b-228">Arrays</span></span>

<span data-ttu-id="95f4b-229">Les tableaux sont également un piège connu dans les types de référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="95f4b-229">Arrays are also a known pitfall in nullable reference types.</span></span> <span data-ttu-id="95f4b-230">Prenons l’exemple suivant qui ne génère pas d’avertissements :</span><span class="sxs-lookup"><span data-stu-id="95f4b-230">Consider the following example which doesn't produce any warnings:</span></span>

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

<span data-ttu-id="95f4b-231">Dans l’exemple précédent, la déclaration du tableau indique qu’elle contient des chaînes qui n’acceptent pas les valeurs NULL, tandis que ses éléments sont tous initialisés à la valeur null.</span><span class="sxs-lookup"><span data-stu-id="95f4b-231">In the preceding example, the declaration of the array shows it holds non-nullable strings, while its elements are all initialized to null.</span></span> <span data-ttu-id="95f4b-232">Ensuite, `s` une valeur null est assignée à la variable (le premier élément du tableau).</span><span class="sxs-lookup"><span data-stu-id="95f4b-232">Then, the variable `s` is assigned a null value (the first element of the array).</span></span> <span data-ttu-id="95f4b-233">Enfin, la variable `s` est déréférencée et provoque une exception Runtime.</span><span class="sxs-lookup"><span data-stu-id="95f4b-233">Finally, the variable `s` is dereferenced causing a runtime exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="95f4b-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95f4b-234">See also</span></span>

- [<span data-ttu-id="95f4b-235">Spécification des types de référence Nullable Draft</span><span class="sxs-lookup"><span data-stu-id="95f4b-235">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [<span data-ttu-id="95f4b-236">Tutoriel d’introduction aux références nullables</span><span class="sxs-lookup"><span data-stu-id="95f4b-236">Intro to nullable references tutorial</span></span>](tutorials/nullable-reference-types.md)
- [<span data-ttu-id="95f4b-237">Migration d’une base de code existante vers des références nullables</span><span class="sxs-lookup"><span data-stu-id="95f4b-237">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="95f4b-238">-Nullable (option du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="95f4b-238">-nullable (C# Compiler option)</span></span>](language-reference/compiler-options/nullable-compiler-option.md)
