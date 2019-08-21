---
title: Utilisation d'espaces de noms - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 32e36a3ebc0de3e5f4a850e0af0261c1e7fd5a07
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039468"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="c926b-102">Utilisation d'espaces de noms (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c926b-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="c926b-103">Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="c926b-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="c926b-104">En premier lieu, les classes .NET Framework utilisent les espaces de noms à des fins d’organisation.</span><span class="sxs-lookup"><span data-stu-id="c926b-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="c926b-105">En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.</span><span class="sxs-lookup"><span data-stu-id="c926b-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="c926b-106">Accès aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c926b-106">Accessing namespaces</span></span>

 <span data-ttu-id="c926b-107">La plupart des applications C# commencent par une section de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="c926b-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="c926b-108">Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c926b-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="c926b-109">Par exemple, en incluant la ligne :</span><span class="sxs-lookup"><span data-stu-id="c926b-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="c926b-110">Au début d’un programme, le programmeur peut utiliser le code :</span><span class="sxs-lookup"><span data-stu-id="c926b-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="c926b-111">À la place de :</span><span class="sxs-lookup"><span data-stu-id="c926b-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="c926b-112">Alias d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="c926b-112">Namespace aliases</span></span>

 <span data-ttu-id="c926b-113">Vous pouvez aussi utiliser la [directive`using`](../../language-reference/keywords/using-directive.md) afin de créer un alias pour un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c926b-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="c926b-114">Utilisez le [qualificateur d'alias d’espace de noms`::`](../../language-reference/operators/namespace-alias-qualifier.md) pour accéder aux membres de l'espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="c926b-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="c926b-115">L'exemple suivant montre comment créer et utiliser un alias d’espace de noms :</span><span class="sxs-lookup"><span data-stu-id="c926b-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="c926b-116">Utilisation d’espaces de noms pour contrôler la portée</span><span class="sxs-lookup"><span data-stu-id="c926b-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="c926b-117">Le mot clé `namespace` est utilisé pour déclarer une portée.</span><span class="sxs-lookup"><span data-stu-id="c926b-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="c926b-118">La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques.</span><span class="sxs-lookup"><span data-stu-id="c926b-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="c926b-119">Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre.</span><span class="sxs-lookup"><span data-stu-id="c926b-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="c926b-120">L’[opérateur `.` d’accès aux membres](../../language-reference/operators/member-access-operators.md#member-access-operator-) est utilisé pour différencier la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="c926b-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="c926b-121">Noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="c926b-121">Fully qualified names</span></span>

 <span data-ttu-id="c926b-122">Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique.</span><span class="sxs-lookup"><span data-stu-id="c926b-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="c926b-123">Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.</span><span class="sxs-lookup"><span data-stu-id="c926b-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="c926b-124">Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="c926b-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="c926b-125">Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.</span><span class="sxs-lookup"><span data-stu-id="c926b-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="c926b-126">Dans le segment de code précédent :</span><span class="sxs-lookup"><span data-stu-id="c926b-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="c926b-127">L’espace de noms `N1` est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="c926b-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="c926b-128">Son nom qualifié complet est `N1`.</span><span class="sxs-lookup"><span data-stu-id="c926b-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="c926b-129">L’espace de noms `N2` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="c926b-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="c926b-130">Son nom qualifié complet est `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="c926b-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="c926b-131">La classe `C1` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="c926b-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="c926b-132">Son nom qualifié complet est `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="c926b-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="c926b-133">Le nom de classe `C2` est utilisé deux fois dans ce code.</span><span class="sxs-lookup"><span data-stu-id="c926b-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="c926b-134">En revanche, les noms qualifiés complets sont uniques.</span><span class="sxs-lookup"><span data-stu-id="c926b-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="c926b-135">La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="c926b-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="c926b-136">La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="c926b-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="c926b-137">À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c926b-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="c926b-138">En règle générale, utilisez le [qualificateur d’alias d’espace de noms `::`](../../language-reference/operators/namespace-alias-qualifier.md) pour référencer un alias d’espace de noms ou `global::` pour référencer l’espace de noms global, et `.` pour qualifier les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="c926b-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="c926b-139">C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c926b-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="c926b-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c926b-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="c926b-141">Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière.</span><span class="sxs-lookup"><span data-stu-id="c926b-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="c926b-142">Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.</span><span class="sxs-lookup"><span data-stu-id="c926b-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="c926b-143">L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias.</span><span class="sxs-lookup"><span data-stu-id="c926b-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="c926b-144">Par exemple, la ligne suivante génère l’avertissement :</span><span class="sxs-lookup"><span data-stu-id="c926b-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="c926b-145">Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c926b-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="c926b-146">Par exemple, prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c926b-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="c926b-147">Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type.</span><span class="sxs-lookup"><span data-stu-id="c926b-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="c926b-148">L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.</span><span class="sxs-lookup"><span data-stu-id="c926b-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c926b-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c926b-149">See also</span></span>

- [<span data-ttu-id="c926b-150">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c926b-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c926b-151">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c926b-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="c926b-152">., opérateur</span><span class="sxs-lookup"><span data-stu-id="c926b-152">. operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="c926b-153">:: opérateur</span><span class="sxs-lookup"><span data-stu-id="c926b-153">:: operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="c926b-154">extern alias</span><span class="sxs-lookup"><span data-stu-id="c926b-154">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
