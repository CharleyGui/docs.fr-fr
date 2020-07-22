---
title: 'Procédure : examiner et instancier des types génériques avec la réflexion'
description: Consultez Comment examiner et instancier des types génériques avec la réflexion. Utilisez les propriétés IsGenericType, IsGenericParameter et GenericParameterPosition.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: b57a0ed0c809da442dc9fcf202ad364060971f80
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865097"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="1f0cc-104">Procédure : examiner et instancier des types génériques avec la réflexion</span><span class="sxs-lookup"><span data-stu-id="1f0cc-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="1f0cc-105">Les informations sur les types génériques s’obtiennent de la même façon que les informations sur les autres types : en examinant un objet <xref:System.Type> qui représente le type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="1f0cc-106">La principale différence est qu’un type générique a une liste d’objets <xref:System.Type> représentant ses paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="1f0cc-107">La première procédure de cette section examine les types génériques.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="1f0cc-108">Vous pouvez créer un objet <xref:System.Type> qui représente un type construit en liant des arguments de type aux paramètres de type d’une définition de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="1f0cc-109">Ceci est illustrée par la deuxième procédure.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="1f0cc-110">Pour examiner un type générique et ses paramètres de type</span><span class="sxs-lookup"><span data-stu-id="1f0cc-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="1f0cc-111">Obtenez une instance de <xref:System.Type> qui représente le type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="1f0cc-112">Dans le code suivant, le type est obtenu à l’aide de l’opérateur C# `typeof` (`GetType` en Visual Basic, `typeid` en Visual C++).</span><span class="sxs-lookup"><span data-stu-id="1f0cc-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="1f0cc-113">Pour découvrir d’autres méthodes d’obtention d’un objet <xref:System.Type>, consultez la rubrique de la classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="1f0cc-114">Notez que dans le reste de cette procédure, le type est contenu dans un paramètre de méthode nommé `t`.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="1f0cc-115">Utilisez la propriété <xref:System.Type.IsGenericType%2A> pour déterminer si le type est générique, et utilisez la propriété <xref:System.Type.IsGenericTypeDefinition%2A> pour déterminer si le type est une définition de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="1f0cc-116">Obtenez un tableau qui contient les arguments de type générique, à l’aide de la méthode <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="1f0cc-117">Pour chaque argument de type, déterminez s’il s’agit d’un paramètre de type (par exemple, dans une définition de type générique) ou d’un type qui a été spécifié pour un paramètre de type (par exemple, dans un type construit), à l’aide de la propriété <xref:System.Type.IsGenericParameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="1f0cc-118">Dans le système de type, un paramètre de type générique est représenté par une instance de <xref:System.Type>, tout comme les types ordinaires.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="1f0cc-119">Le code suivant affiche le nom et la position du paramètre d’un objet <xref:System.Type> qui représente un paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="1f0cc-120">La position di paramètre est ici sans importance. Elle est plus utile quand vous examinez un paramètre de type qui a été utilisé comme argument de type d’un autre type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="1f0cc-121">Déterminez la contrainte de type de base et les contraintes d’interface d’un paramètre de type générique en utilisant la méthode <xref:System.Type.GetGenericParameterConstraints%2A> pour obtenir toutes les contraintes dans un seul tableau.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="1f0cc-122">L’ordre des contraintes n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="1f0cc-123">Utilisez la propriété <xref:System.Type.GenericParameterAttributes%2A> pour découvrir les contraintes spéciales d’un paramètre de type, telles que l’obligation d’être un type référence.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="1f0cc-124">La propriété inclut également des valeurs qui représentent la variance, que vous pouvez masquer comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="1f0cc-125">Les attributs de contrainte spéciales sont des indicateurs, et l’indicateur (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) qui ne représente aucune contrainte spéciale représente également aucune covariance ou contravariance.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="1f0cc-126">Ainsi, pour tester l’une de ces conditions, vous devez utiliser le masque approprié.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="1f0cc-127">Dans ce cas, utilisez <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> pour isoler les indicateurs de contraintes spéciales.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="1f0cc-128">Construction d’une instance d’un type générique</span><span class="sxs-lookup"><span data-stu-id="1f0cc-128">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="1f0cc-129">Un type générique est comme un modèle.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-129">A generic type is like a template.</span></span> <span data-ttu-id="1f0cc-130">Vous ne pouvez pas créer des instances de ce type, sauf si vous spécifiez des types réels pour ses paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="1f0cc-131">Effectuer cela au moment de l’exécution à l’aide de la réflexion nécessite la méthode <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="1f0cc-132">Pour construire une instance d’un type générique</span><span class="sxs-lookup"><span data-stu-id="1f0cc-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="1f0cc-133">Obtenez un objet <xref:System.Type> qui représente le type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="1f0cc-134">Le code suivant obtient le type générique <xref:System.Collections.Generic.Dictionary%602> de deux manières différentes : en utilisant la surcharge de méthode <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> avec une chaîne qui décrit le type, et en appelant la méthode <xref:System.Type.GetGenericTypeDefinition%2A> sur le type construit `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1f0cc-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="1f0cc-135">La méthode <xref:System.Type.MakeGenericType%2A> nécessite une définition de type générique.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="1f0cc-136">Créez un tableau d’arguments de type pour remplacer les paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="1f0cc-137">Le tableau doit contenir le nombre correct d’objets <xref:System.Type>, dans l’ordre où ils apparaissent dans la liste de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="1f0cc-138">Dans ce cas, la clé (premier paramètre de type) est de type <xref:System.String>, et les valeurs dans le dictionnaire sont des instances d’une classe nommée `Example`.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="1f0cc-139">Appelez la méthode <xref:System.Type.MakeGenericType%2A> pour lier les arguments de type aux paramètres de type et construire le type.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="1f0cc-140">Utilisez la surcharge de méthode <xref:System.Activator.CreateInstance%28System.Type%29> pour créer un objet du type construit.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="1f0cc-141">Le code suivant stocke deux instances de la classe `Example` dans l’objet `Dictionary<String, Example>` obtenu.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="1f0cc-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f0cc-142">Example</span></span>  
 <span data-ttu-id="1f0cc-143">L’exemple de code suivant définit une méthode `DisplayGenericType` pour examiner les définitions de type générique et les types construits utilisés dans le code, et pour afficher leurs informations.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="1f0cc-144">La méthode `DisplayGenericType` montre comment utiliser les propriétés <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> et <xref:System.Type.GenericParameterPosition%2A>, et la méthode <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="1f0cc-145">L’exemple définit également une méthode `DisplayGenericParameter` pour examiner un paramètre de type générique et afficher ses contraintes.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="1f0cc-146">L’exemple de code définit un ensemble de types de test, notamment un type générique qui illustre des contraintes de paramètre de type, et montre comment afficher des informations sur ces types.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="1f0cc-147">L’exemple construit un type à partir de la classe <xref:System.Collections.Generic.Dictionary%602> en créant un tableau d’arguments de type et en appelant la méthode <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="1f0cc-148">Le programme compare l’objet <xref:System.Type> construit à l’aide de <xref:System.Type.MakeGenericType%2A> avec un objet <xref:System.Type> obtenu à l’aide de `typeof` (`GetType` en Visual Basic), et démontre qu’ils sont identiques.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="1f0cc-149">De même, le programme utilise la méthode <xref:System.Type.GetGenericTypeDefinition%2A> pour obtenir la définition de type générique du type construit, et la compare à l’objet <xref:System.Type> représentant la classe <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="1f0cc-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1f0cc-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f0cc-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="1f0cc-151">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="1f0cc-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="1f0cc-152">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="1f0cc-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="1f0cc-153">Génériques</span><span class="sxs-lookup"><span data-stu-id="1f0cc-153">Generics</span></span>](../../standard/generics/index.md)
