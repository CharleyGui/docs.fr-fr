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
ms.openlocfilehash: abd4c34661d96d8c3188e92dd2d76f847e17aae7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433537"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="bd851-102">Utilisation d'espaces de noms (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bd851-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="bd851-103">Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="bd851-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="bd851-104">En premier lieu, les classes .NET Framework utilisent les espaces de noms à des fins d’organisation.</span><span class="sxs-lookup"><span data-stu-id="bd851-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="bd851-105">En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.</span><span class="sxs-lookup"><span data-stu-id="bd851-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="bd851-106">Accès aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="bd851-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="bd851-107">La plupart des applications C# commencent par une section de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="bd851-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="bd851-108">Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bd851-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="bd851-109">Par exemple, en incluant la ligne :</span><span class="sxs-lookup"><span data-stu-id="bd851-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="bd851-110">Au début d’un programme, le programmeur peut utiliser le code :</span><span class="sxs-lookup"><span data-stu-id="bd851-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="bd851-111">À la place de :</span><span class="sxs-lookup"><span data-stu-id="bd851-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="bd851-112">Alias d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="bd851-112">Namespace Aliases</span></span>  
 <span data-ttu-id="bd851-113">La [directive using](../../../csharp/language-reference/keywords/using-directive.md) peut aussi servir à créer un alias pour un [espace de noms](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="bd851-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="bd851-114">Par exemple, si vous utilisez un espace de noms écrit précédemment qui contient des espaces de noms imbriqués, vous pouvez déclarer un alias pour offrir un moyen rapide d’en référencer un en particulier, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bd851-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="bd851-115">Utilisation d’espaces de noms pour contrôler la portée</span><span class="sxs-lookup"><span data-stu-id="bd851-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="bd851-116">Le mot clé `namespace` est utilisé pour déclarer une portée.</span><span class="sxs-lookup"><span data-stu-id="bd851-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="bd851-117">La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques.</span><span class="sxs-lookup"><span data-stu-id="bd851-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="bd851-118">Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre.</span><span class="sxs-lookup"><span data-stu-id="bd851-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="bd851-119">L’[opérateur `.` d’accès aux membres](../../language-reference/operators/member-access-operators.md#member-access-operator-) est utilisé pour différencier la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="bd851-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="bd851-120">noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="bd851-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="bd851-121">Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique.</span><span class="sxs-lookup"><span data-stu-id="bd851-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="bd851-122">Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.</span><span class="sxs-lookup"><span data-stu-id="bd851-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="bd851-123">Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="bd851-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="bd851-124">Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.</span><span class="sxs-lookup"><span data-stu-id="bd851-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="bd851-125">Dans le segment de code précédent :</span><span class="sxs-lookup"><span data-stu-id="bd851-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="bd851-126">L’espace de noms `N1` est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="bd851-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="bd851-127">Son nom qualifié complet est `N1`.</span><span class="sxs-lookup"><span data-stu-id="bd851-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="bd851-128">L’espace de noms `N2` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="bd851-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="bd851-129">Son nom qualifié complet est `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="bd851-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="bd851-130">La classe `C1` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="bd851-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="bd851-131">Son nom qualifié complet est `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="bd851-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="bd851-132">Le nom de classe `C2` est utilisé deux fois dans ce code.</span><span class="sxs-lookup"><span data-stu-id="bd851-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="bd851-133">En revanche, les noms qualifiés complets sont uniques.</span><span class="sxs-lookup"><span data-stu-id="bd851-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="bd851-134">La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="bd851-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="bd851-135">La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="bd851-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="bd851-136">À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="bd851-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="bd851-137">En règle générale, utilisez `::` pour faire référence à un alias d’espace de noms ou `global::` pour faire référence à l’espace de noms global et `.` pour qualifier les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="bd851-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="bd851-138">C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bd851-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="bd851-139">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bd851-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="bd851-140">Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière.</span><span class="sxs-lookup"><span data-stu-id="bd851-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="bd851-141">Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.</span><span class="sxs-lookup"><span data-stu-id="bd851-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="bd851-142">L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias.</span><span class="sxs-lookup"><span data-stu-id="bd851-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="bd851-143">Par exemple, la ligne suivante génère l’avertissement :</span><span class="sxs-lookup"><span data-stu-id="bd851-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="bd851-144">Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="bd851-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="bd851-145">Par exemple, prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bd851-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="bd851-146">Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type.</span><span class="sxs-lookup"><span data-stu-id="bd851-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="bd851-147">L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.</span><span class="sxs-lookup"><span data-stu-id="bd851-147">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="bd851-148">Consultez la rubrique [Guide pratique pour utiliser l’alias d’espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) pour plus d’informations sur l’alias `global`.</span><span class="sxs-lookup"><span data-stu-id="bd851-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd851-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd851-149">See also</span></span>

- [<span data-ttu-id="bd851-150">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bd851-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bd851-151">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="bd851-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="bd851-152">. Opérateur</span><span class="sxs-lookup"><span data-stu-id="bd851-152">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="bd851-153">:: Opérateur</span><span class="sxs-lookup"><span data-stu-id="bd851-153">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="bd851-154">extern</span><span class="sxs-lookup"><span data-stu-id="bd851-154">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
