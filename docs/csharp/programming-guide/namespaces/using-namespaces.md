---
title: Utilisation d'espaces de noms - Guide de programmation C#
description: Découvrez comment utiliser des espaces de noms en programmation C#, tels que l’accès aux espaces de noms, les alias d’espaces de noms et l’utilisation d’espaces de noms pour contrôler la portée.
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 86892f50e059c16ee9c133d7ba9f2716e11a8e56
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381695"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="159d6-103">Utilisation d'espaces de noms (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="159d6-103">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="159d6-104">Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="159d6-104">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="159d6-105">Tout d’abord, les classes .NET utilisent des espaces de noms pour organiser ses nombreuses classes.</span><span class="sxs-lookup"><span data-stu-id="159d6-105">Firstly, the .NET classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="159d6-106">En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.</span><span class="sxs-lookup"><span data-stu-id="159d6-106">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="159d6-107">Accès aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="159d6-107">Accessing namespaces</span></span>

 <span data-ttu-id="159d6-108">La plupart des applications C# commencent par une section de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="159d6-108">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="159d6-109">Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.</span><span class="sxs-lookup"><span data-stu-id="159d6-109">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="159d6-110">Par exemple, en incluant la ligne :</span><span class="sxs-lookup"><span data-stu-id="159d6-110">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="159d6-111">Au début d’un programme, le programmeur peut utiliser le code :</span><span class="sxs-lookup"><span data-stu-id="159d6-111">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="159d6-112">À la place de :</span><span class="sxs-lookup"><span data-stu-id="159d6-112">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="159d6-113">Alias d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="159d6-113">Namespace aliases</span></span>

 <span data-ttu-id="159d6-114">Vous pouvez également utiliser la [ `using` directive](../../language-reference/keywords/using-directive.md) pour créer un alias pour un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="159d6-114">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="159d6-115">Utilisez le [qualificateur d'alias d’espace de noms`::`](../../language-reference/operators/namespace-alias-qualifier.md) pour accéder aux membres de l'espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="159d6-115">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="159d6-116">L'exemple suivant montre comment créer et utiliser un alias d’espace de noms :</span><span class="sxs-lookup"><span data-stu-id="159d6-116">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="159d6-117">Utilisation d’espaces de noms pour contrôler la portée</span><span class="sxs-lookup"><span data-stu-id="159d6-117">Using namespaces to control scope</span></span>

 <span data-ttu-id="159d6-118">Le mot clé `namespace` est utilisé pour déclarer une portée.</span><span class="sxs-lookup"><span data-stu-id="159d6-118">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="159d6-119">La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques.</span><span class="sxs-lookup"><span data-stu-id="159d6-119">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="159d6-120">Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre.</span><span class="sxs-lookup"><span data-stu-id="159d6-120">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="159d6-121">Le [ `.` jeton](../../language-reference/operators/member-access-operators.md#member-access-expression-) est utilisé pour distinguer la méthode qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="159d6-121">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="159d6-122">Noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="159d6-122">Fully qualified names</span></span>

 <span data-ttu-id="159d6-123">Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique.</span><span class="sxs-lookup"><span data-stu-id="159d6-123">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="159d6-124">Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.</span><span class="sxs-lookup"><span data-stu-id="159d6-124">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="159d6-125">Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="159d6-125">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="159d6-126">Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.</span><span class="sxs-lookup"><span data-stu-id="159d6-126">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="159d6-127">Dans le segment de code précédent :</span><span class="sxs-lookup"><span data-stu-id="159d6-127">In the previous code segment:</span></span>  
  
- <span data-ttu-id="159d6-128">L’espace de noms `N1` est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="159d6-128">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="159d6-129">Son nom qualifié complet est `N1`.</span><span class="sxs-lookup"><span data-stu-id="159d6-129">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="159d6-130">L’espace de noms `N2` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="159d6-130">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="159d6-131">Son nom qualifié complet est `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="159d6-131">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="159d6-132">La classe `C1` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="159d6-132">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="159d6-133">Son nom qualifié complet est `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="159d6-133">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="159d6-134">Le nom de classe `C2` est utilisé deux fois dans ce code.</span><span class="sxs-lookup"><span data-stu-id="159d6-134">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="159d6-135">En revanche, les noms qualifiés complets sont uniques.</span><span class="sxs-lookup"><span data-stu-id="159d6-135">However, the fully qualified names are unique.</span></span> <span data-ttu-id="159d6-136">La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="159d6-136">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="159d6-137">La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="159d6-137">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="159d6-138">À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="159d6-138">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="159d6-139">En règle générale, utilisez le [qualificateur d’alias d’espace de noms `::`](../../language-reference/operators/namespace-alias-qualifier.md) pour référencer un alias d’espace de noms ou `global::` pour référencer l’espace de noms global, et `.` pour qualifier les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="159d6-139">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="159d6-140">C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="159d6-140">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="159d6-141">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="159d6-141">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="159d6-142">Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière.</span><span class="sxs-lookup"><span data-stu-id="159d6-142">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="159d6-143">Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.</span><span class="sxs-lookup"><span data-stu-id="159d6-143">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="159d6-144">L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias.</span><span class="sxs-lookup"><span data-stu-id="159d6-144">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="159d6-145">Par exemple, la ligne suivante génère l’avertissement :</span><span class="sxs-lookup"><span data-stu-id="159d6-145">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="159d6-146">Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="159d6-146">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="159d6-147">Par exemple, prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="159d6-147">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="159d6-148">Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type.</span><span class="sxs-lookup"><span data-stu-id="159d6-148">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="159d6-149">L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.</span><span class="sxs-lookup"><span data-stu-id="159d6-149">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="159d6-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="159d6-150">See also</span></span>

- [<span data-ttu-id="159d6-151">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="159d6-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="159d6-152">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="159d6-152">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="159d6-153">Expression d’accès au membre</span><span class="sxs-lookup"><span data-stu-id="159d6-153">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="159d6-154">:: (opérateur)</span><span class="sxs-lookup"><span data-stu-id="159d6-154">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="159d6-155">extern alias</span><span class="sxs-lookup"><span data-stu-id="159d6-155">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
