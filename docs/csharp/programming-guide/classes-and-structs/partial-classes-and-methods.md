---
title: Classes et méthodes partielles - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 0a0cf7c3b6024f75196abed5fdb7d18a058c58db
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398380"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="a4641-102">Classes et méthodes partielles (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a4641-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="a4641-103">Il est possible de fractionner la définition d’une [classe](../../../csharp/language-reference/keywords/class.md), d’un [struct](../../../csharp/language-reference/keywords/struct.md), d’une [interface](../../../csharp/language-reference/keywords/interface.md) ou d’une méthode entre plusieurs fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="a4641-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="a4641-104">Chaque fichier source contient une section de la définition de méthode ou de type, et toutes les parties sont combinées au moment où l’application est compilée.</span><span class="sxs-lookup"><span data-stu-id="a4641-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="a4641-105">Classes partielles</span><span class="sxs-lookup"><span data-stu-id="a4641-105">Partial Classes</span></span>

<span data-ttu-id="a4641-106">Il peut être utile de fractionner une définition de classe dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4641-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="a4641-107">Dans des projets volumineux, le fractionnement d’une classe entre plusieurs fichiers distincts permet à plusieurs programmeurs d’y travailler simultanément.</span><span class="sxs-lookup"><span data-stu-id="a4641-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="a4641-108">Quand vous utilisez une source générée automatiquement, vous pouvez ajouter du code à la classe sans avoir à recréer le fichier source.</span><span class="sxs-lookup"><span data-stu-id="a4641-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="a4641-109">Visual Studio suit cette approche pour créer des formulaires Windows Forms, du code wrapper de service web, etc.</span><span class="sxs-lookup"><span data-stu-id="a4641-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="a4641-110">Vous pouvez écrire du code qui utilise ces classes sans avoir à modifier le fichier créé par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4641-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="a4641-111">Pour fractionner une définition de classe, utilisez le modificateur de mot clé [partial](../../../csharp/language-reference/keywords/partial-type.md), comme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a4641-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="a4641-112">Le mot clé `partial` indique que d’autres parties de la classe, du struct ou de l’interface peuvent être définies dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="a4641-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="a4641-113">Toutes les parties doivent utiliser le mot clé `partial`.</span><span class="sxs-lookup"><span data-stu-id="a4641-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="a4641-114">Toutes les parties doivent être disponibles à la compilation pour former le type final.</span><span class="sxs-lookup"><span data-stu-id="a4641-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="a4641-115">Toutes les parties doivent avoir la même accessibilité : `public`, `private`, etc.</span><span class="sxs-lookup"><span data-stu-id="a4641-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="a4641-116">Si une partie est déclarée comme abstract, l’ensemble du type est considéré comme abstract.</span><span class="sxs-lookup"><span data-stu-id="a4641-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="a4641-117">Si une partie est déclarée comme sealed, l’ensemble du type est considéré comme sealed.</span><span class="sxs-lookup"><span data-stu-id="a4641-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="a4641-118">Si une partie déclare un type de base, l’ensemble du type hérite de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a4641-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="a4641-119">Toutes les parties qui spécifient une classe de base doivent être en accord, mais les parties qui omettent une classe de base héritent tout de même du type de base.</span><span class="sxs-lookup"><span data-stu-id="a4641-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="a4641-120">Les parties peuvent spécifier des interfaces de base différentes. Le type final implémente alors toutes les interfaces indiquées dans toutes les déclarations partielles.</span><span class="sxs-lookup"><span data-stu-id="a4641-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="a4641-121">Tous les membres de classe, de struct ou d’interface déclarés dans une définition partielle sont disponibles pour toutes les autres parties.</span><span class="sxs-lookup"><span data-stu-id="a4641-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="a4641-122">Le type final est la combinaison de toutes les parties au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a4641-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="a4641-123">Le modificateur `partial` n’est pas disponible sur les déclarations de délégué ou d’énumération.</span><span class="sxs-lookup"><span data-stu-id="a4641-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="a4641-124">L’exemple suivant montre que les types imbriqués peuvent être partiels, même si le type dans lequel ils sont imbriqués n’est pas partiel lui-même.</span><span class="sxs-lookup"><span data-stu-id="a4641-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="a4641-125">Au moment de la compilation, les attributs de définitions de type partiel sont fusionnés.</span><span class="sxs-lookup"><span data-stu-id="a4641-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="a4641-126">Observez, par exemple, les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4641-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="a4641-127">Elles sont équivalentes aux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4641-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="a4641-128">Les éléments suivants sont fusionnés à partir de toutes les définitions de type partiel :</span><span class="sxs-lookup"><span data-stu-id="a4641-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="a4641-129">commentaires XML</span><span class="sxs-lookup"><span data-stu-id="a4641-129">XML comments</span></span>

- <span data-ttu-id="a4641-130">interfaces</span><span class="sxs-lookup"><span data-stu-id="a4641-130">interfaces</span></span>

- <span data-ttu-id="a4641-131">attributs de paramètre de type générique</span><span class="sxs-lookup"><span data-stu-id="a4641-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="a4641-132">attributs de classe</span><span class="sxs-lookup"><span data-stu-id="a4641-132">class attributes</span></span>

- <span data-ttu-id="a4641-133">membres</span><span class="sxs-lookup"><span data-stu-id="a4641-133">members</span></span>

<span data-ttu-id="a4641-134">Observez, par exemple, les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4641-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="a4641-135">Elles sont équivalentes aux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4641-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="a4641-136">Restrictions</span><span class="sxs-lookup"><span data-stu-id="a4641-136">Restrictions</span></span>

<span data-ttu-id="a4641-137">Il y a plusieurs règles à respecter quand vous utilisez des définitions de classe partielle :</span><span class="sxs-lookup"><span data-stu-id="a4641-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="a4641-138">Toutes les définitions de type partiel conçues comme des parties du même type doivent être modifiées avec `partial`.</span><span class="sxs-lookup"><span data-stu-id="a4641-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="a4641-139">Par exemple, les déclarations de classe suivantes génèrent une erreur :</span><span class="sxs-lookup"><span data-stu-id="a4641-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="a4641-140">Le modificateur `partial` peut uniquement être placé juste avant les mots clés `class`, `struct` ou `interface`.</span><span class="sxs-lookup"><span data-stu-id="a4641-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="a4641-141">Les types partiels imbriqués sont autorisés dans les définitions de type partiel, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a4641-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="a4641-142">Toutes les définitions de type partiel conçues comme des parties du même type doivent être définies dans le même assembly et dans le même module (fichier .exe ou .dll).</span><span class="sxs-lookup"><span data-stu-id="a4641-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="a4641-143">Les définitions partielles ne peuvent pas être fractionnées entre plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="a4641-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="a4641-144">Le nom de classe et les paramètres de type générique doivent correspondre dans toutes les définitions de type partiel.</span><span class="sxs-lookup"><span data-stu-id="a4641-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="a4641-145">Les types génériques peuvent être partiels.</span><span class="sxs-lookup"><span data-stu-id="a4641-145">Generic types can be partial.</span></span> <span data-ttu-id="a4641-146">Chaque déclaration partielle doit utiliser les mêmes noms de paramètres, dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="a4641-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="a4641-147">Les mots clés suivants sont facultatifs dans une définition de type partiel. S’ils sont utilisés dans une définition de type partiel, ils ne doivent pas être en conflit avec les mots clés spécifiés dans une autre définition partielle pour le même type :</span><span class="sxs-lookup"><span data-stu-id="a4641-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="a4641-148">public</span><span class="sxs-lookup"><span data-stu-id="a4641-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)

  - [<span data-ttu-id="a4641-149">private</span><span class="sxs-lookup"><span data-stu-id="a4641-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)

  - [<span data-ttu-id="a4641-150">protected</span><span class="sxs-lookup"><span data-stu-id="a4641-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)

  - [<span data-ttu-id="a4641-151">internal</span><span class="sxs-lookup"><span data-stu-id="a4641-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

  - [<span data-ttu-id="a4641-152">abstract</span><span class="sxs-lookup"><span data-stu-id="a4641-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)

  - [<span data-ttu-id="a4641-153">sealed</span><span class="sxs-lookup"><span data-stu-id="a4641-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)

  - <span data-ttu-id="a4641-154">classe de base</span><span class="sxs-lookup"><span data-stu-id="a4641-154">base class</span></span>

  - <span data-ttu-id="a4641-155">modificateur [new](../../../csharp/language-reference/keywords/new-modifier.md) (parties imbriquées)</span><span class="sxs-lookup"><span data-stu-id="a4641-155">[new](../../../csharp/language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="a4641-156">contraintes génériques</span><span class="sxs-lookup"><span data-stu-id="a4641-156">generic constraints</span></span>

<span data-ttu-id="a4641-157">Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="a4641-158">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="a4641-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="a4641-159">Description</span><span class="sxs-lookup"><span data-stu-id="a4641-159">Description</span></span>

<span data-ttu-id="a4641-160">Dans l’exemple suivant, les champs et le constructeur de la classe `Coords` sont déclarés dans une définition de classe partielle, et le membre `PrintCoords` est déclaré dans une autre définition de classe partielle.</span><span class="sxs-lookup"><span data-stu-id="a4641-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="a4641-161">Code</span><span class="sxs-lookup"><span data-stu-id="a4641-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="a4641-162">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="a4641-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="a4641-163">Description</span><span class="sxs-lookup"><span data-stu-id="a4641-163">Description</span></span>

<span data-ttu-id="a4641-164">L’exemple suivant montre que vous pouvez également développer des interfaces et des structs partiels.</span><span class="sxs-lookup"><span data-stu-id="a4641-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="a4641-165">Code</span><span class="sxs-lookup"><span data-stu-id="a4641-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="a4641-166">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="a4641-166">Partial Methods</span></span>

<span data-ttu-id="a4641-167">Une classe partielle ou un struct partiel peut contenir une méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="a4641-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="a4641-168">Une partie de la classe contient la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4641-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="a4641-169">Une implémentation facultative peut être définie dans la même partie ou dans une autre partie.</span><span class="sxs-lookup"><span data-stu-id="a4641-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="a4641-170">Si l’implémentation n’est pas fournie, la méthode et tous les appels à cette méthode sont supprimés au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a4641-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="a4641-171">Les méthodes partielles permettent à l’implémenteur d’une partie d’une classe de définir une méthode, comme pour un événement.</span><span class="sxs-lookup"><span data-stu-id="a4641-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="a4641-172">L’implémenteur de l’autre partie de la classe peut décider s’il faut implémenter la méthode ou non.</span><span class="sxs-lookup"><span data-stu-id="a4641-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="a4641-173">Si la méthode n’est pas implémentée, le compilateur supprime la signature de méthode et tous les appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4641-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="a4641-174">Les appels à la méthode, y compris tous les résultats retournés par l’évaluation des arguments dans les appels, n’ont aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a4641-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="a4641-175">C’est pourquoi le code dans la classe partielle peut utiliser librement une méthode partielle, même si l’implémentation n’est pas fournie.</span><span class="sxs-lookup"><span data-stu-id="a4641-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="a4641-176">Aucune erreur de compilation ou d’exécution n’est générée si la méthode est appelée, mais qu’elle n’est pas finalement implémentée.</span><span class="sxs-lookup"><span data-stu-id="a4641-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="a4641-177">Les méthodes partielles sont particulièrement utiles pour personnaliser le code généré.</span><span class="sxs-lookup"><span data-stu-id="a4641-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="a4641-178">Elles permettent de réserver un nom et une signature de méthode. Ainsi, le code généré peut appeler la méthode, mais le développeur peut décider d’implémenter ou non la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4641-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="a4641-179">En grande partie comme les classes partielles, les méthodes partielles permettent d’utiliser conjointement du code créé par un générateur de code et du code créé manuellement par un développeur sans impact sur le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a4641-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="a4641-180">Une déclaration de méthode partielle se compose de deux parties : la définition et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a4641-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="a4641-181">Celles-ci peuvent être situées dans des parties distinctes ou dans la même partie d’une classe partielle.</span><span class="sxs-lookup"><span data-stu-id="a4641-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="a4641-182">En l’absence de déclaration d’implémentation, le compilateur optimise à la fois la déclaration de définition et tous les appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4641-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="a4641-183">Une déclaration de méthode partielle doit commencer par le mot clé contextuel [partial](../../../csharp/language-reference/keywords/partial-type.md), et la méthode doit retourner [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>

- <span data-ttu-id="a4641-184">Les méthodes partielles peuvent avoir des paramètres [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) ou [ref](../../../csharp/language-reference/keywords/ref.md), mais pas [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="a4641-185">Les méthodes partielles sont implicitement [private](../../../csharp/language-reference/keywords/private.md) et, par conséquent, elles ne peuvent pas être [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="a4641-186">Les méthodes partielles ne peuvent pas être [extern](../../../csharp/language-reference/keywords/extern.md), car la présence du corps détermine si elles sont utilisées pour la définition ou pour l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a4641-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="a4641-187">Les méthodes partielles peuvent avoir des modificateurs [static](../../../csharp/language-reference/keywords/static.md) et [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="a4641-188">Les méthodes partielles peuvent être génériques.</span><span class="sxs-lookup"><span data-stu-id="a4641-188">Partial methods can be generic.</span></span> <span data-ttu-id="a4641-189">Les contraintes sont placées sur la déclaration de méthode partielle de définition et peuvent être répétées facultativement sur la déclaration d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a4641-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="a4641-190">Les noms de paramètre et de paramètre de type ne doivent pas obligatoirement être identiques dans la déclaration d’implémentation et la déclaration de définition.</span><span class="sxs-lookup"><span data-stu-id="a4641-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="a4641-191">Vous pouvez créer un [délégué](../../../csharp/language-reference/keywords/delegate.md) pour une méthode partielle qui a été définie et implémentée, mais pas pour une méthode partielle qui a uniquement été définie.</span><span class="sxs-lookup"><span data-stu-id="a4641-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a4641-192">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a4641-192">C# Language Specification</span></span>

<span data-ttu-id="a4641-193">Pour plus d’informations, consultez [Types partiels](~/_csharplang/spec/classes.md#partial-types) dans la [spécification du langage C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4641-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="a4641-194">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="a4641-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4641-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4641-195">See also</span></span>

- [<span data-ttu-id="a4641-196">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a4641-196">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a4641-197">Classes</span><span class="sxs-lookup"><span data-stu-id="a4641-197">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="a4641-198">Structs</span><span class="sxs-lookup"><span data-stu-id="a4641-198">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="a4641-199">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a4641-199">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="a4641-200">partial (type)</span><span class="sxs-lookup"><span data-stu-id="a4641-200">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
