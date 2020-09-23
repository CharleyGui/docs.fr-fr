---
title: Types génériques
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: f9b343c664baaf316e5cd6df72da8dcf56222382
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090259"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="dd40f-102">Types génériques Visual Basic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd40f-102">Generic Types in Visual Basic (Visual Basic)</span></span>

<span data-ttu-id="dd40f-103">Un *type générique* est un élément de programmation unique qui s’adapte pour exécuter la même fonction sur différents types de données.</span><span class="sxs-lookup"><span data-stu-id="dd40f-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="dd40f-104">Quand vous définissez une classe ou procédure générique, vous n’avez pas besoin de définir une version distincte pour chaque type de données pour lequel vous voulez exécuter la fonction.</span><span class="sxs-lookup"><span data-stu-id="dd40f-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="dd40f-105">On pourrait comparer cet élément de programmation à un tournevis à têtes interchangeables.</span><span class="sxs-lookup"><span data-stu-id="dd40f-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="dd40f-106">Vous examinez quel type de vis vous devez serrer et vous choisissez la tête de vis adaptée (fendue, cruciforme, en étoile).</span><span class="sxs-lookup"><span data-stu-id="dd40f-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="dd40f-107">Quelle que soit la tête insérée dans le manche du tournevis, vous exécutez toujours la même fonction : vous serrez une vis.</span><span class="sxs-lookup"><span data-stu-id="dd40f-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 ![Diagramme d’un tournevis défini avec des têtes différentes.](./media/generic-types/generic-screwdriver-set.gif)  
  
 <span data-ttu-id="dd40f-109">Quand vous définissez un type générique, vous devez le paramétrer avec un ou plusieurs types de données.</span><span class="sxs-lookup"><span data-stu-id="dd40f-109">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="dd40f-110">Cela permet au code utilisé d’adapter les types de données à ses besoins.</span><span class="sxs-lookup"><span data-stu-id="dd40f-110">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="dd40f-111">Votre code peut déclarer plusieurs éléments de programmation différents à partir de l’élément générique, chacun d’eux agissant sur un ensemble différent de types de données.</span><span class="sxs-lookup"><span data-stu-id="dd40f-111">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="dd40f-112">Ces éléments déclarés exécutent tous la même logique, quel que soit le type de données qu’ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="dd40f-112">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="dd40f-113">Par exemple, vous pouvez créer et utiliser une classe « queue » qui agit sur un type de données spécifique, tel que `String`.</span><span class="sxs-lookup"><span data-stu-id="dd40f-113">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="dd40f-114">Vous pouvez déclarer cette classe à partir de <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dd40f-114">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="dd40f-115">Vous pouvez maintenant utiliser `stringQ` pour agir uniquement sur des valeurs `String` .</span><span class="sxs-lookup"><span data-stu-id="dd40f-115">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="dd40f-116">Étant donné que `stringQ` est spécifique aux valeurs `String` au lieu d’être généralisé pour les valeurs `Object` , aucune liaison tardive ou conversion de type n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dd40f-116">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="dd40f-117">Cela permet de réduire le délai d’exécution et les erreurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd40f-117">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="dd40f-118">Pour plus d’informations sur l’utilisation d’un type générique, consultez [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span><span class="sxs-lookup"><span data-stu-id="dd40f-118">For more information on using a generic type, see [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="dd40f-119">Exemple d’une classe générique</span><span class="sxs-lookup"><span data-stu-id="dd40f-119">Example of a Generic Class</span></span>  

 <span data-ttu-id="dd40f-120">L’exemple suivant présente une définition squelette d’une classe générique.</span><span class="sxs-lookup"><span data-stu-id="dd40f-120">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="dd40f-121">Dans le squelette ci-dessus, `t` est un *paramètre de type*, c’est-à-dire un espace réservé pour un type de données que vous fournissez quand vous déclarez la classe.</span><span class="sxs-lookup"><span data-stu-id="dd40f-121">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="dd40f-122">Ailleurs dans votre code, vous pouvez déclarer des versions différentes de `classHolder` en fournissant différents types de données pour `t`.</span><span class="sxs-lookup"><span data-stu-id="dd40f-122">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="dd40f-123">L’exemple suivant illustre deux déclarations.</span><span class="sxs-lookup"><span data-stu-id="dd40f-123">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="dd40f-124">Les instructions ci-dessus déclarent des *classes construites*, dans lesquelles un type spécifique remplace le paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-124">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="dd40f-125">Ce remplacement est propagé partout dans le code de la classe construite.</span><span class="sxs-lookup"><span data-stu-id="dd40f-125">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="dd40f-126">L’exemple suivant montre à quoi ressemble la procédure `processNewItem` dans `integerClass`.</span><span class="sxs-lookup"><span data-stu-id="dd40f-126">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="dd40f-127">Pour obtenir un exemple plus complet, consultez [Comment : définir une classe qui peut fournir des fonctionnalités identiques sur différents types de données](how-to-define-a-class-that-can-provide-identical-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="dd40f-127">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="dd40f-128">Éléments de programmation disponibles</span><span class="sxs-lookup"><span data-stu-id="dd40f-128">Eligible Programming Elements</span></span>  

 <span data-ttu-id="dd40f-129">Vous pouvez définir et utiliser des délégués, structures, interfaces, procédures et classes génériques.</span><span class="sxs-lookup"><span data-stu-id="dd40f-129">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="dd40f-130">Notez que le .NET Framework définit plusieurs classes, structures et interfaces génériques qui représentent des éléments génériques couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="dd40f-130">Note that the .NET Framework defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="dd40f-131">L’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> fournit des dictionnaires, des listes, des files d’attente et des piles.</span><span class="sxs-lookup"><span data-stu-id="dd40f-131">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="dd40f-132">Avant de définir votre propre élément générique, vérifiez s’il est disponible dans <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd40f-132">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="dd40f-133">Les procédures ne sont pas des types, mais vous pouvez définir et utiliser des procédures génériques.</span><span class="sxs-lookup"><span data-stu-id="dd40f-133">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="dd40f-134">Consultez [Generic Procedures in Visual Basic](generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dd40f-134">See [Generic Procedures in Visual Basic](generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="dd40f-135">Avantages des types génériques</span><span class="sxs-lookup"><span data-stu-id="dd40f-135">Advantages of Generic Types</span></span>  

 <span data-ttu-id="dd40f-136">Un type générique sert de base de déclaration de plusieurs éléments de programmation différents, chacun agissant sur un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="dd40f-136">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="dd40f-137">À la place d’un type générique, vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="dd40f-137">The alternatives to a generic type are:</span></span>  
  
1. <span data-ttu-id="dd40f-138">un type unique pour le type de données `Object` ;</span><span class="sxs-lookup"><span data-stu-id="dd40f-138">A single type operating on the `Object` data type.</span></span>  
  
2. <span data-ttu-id="dd40f-139">Ensemble de versions *spécifiques au type* du type, chaque version étant individuellement codée et opérant sur un type de données spécifique tel que `String` , `Integer` ou un type défini par l’utilisateur tel que `customer` .</span><span class="sxs-lookup"><span data-stu-id="dd40f-139">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="dd40f-140">Un type générique présente les avantages suivants par rapport à ces alternatives :</span><span class="sxs-lookup"><span data-stu-id="dd40f-140">A generic type has the following advantages over these alternatives:</span></span>  
  
- <span data-ttu-id="dd40f-141">**Sécurité de type.**</span><span class="sxs-lookup"><span data-stu-id="dd40f-141">**Type Safety.**</span></span> <span data-ttu-id="dd40f-142">. Avec les types génériques, une vérification des types est effectuée au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="dd40f-142">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="dd40f-143">Les types basés sur `Object` acceptent tous les types de données. Vous devez écrire le code permettant de vérifier si un type de données d’entrée est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="dd40f-143">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="dd40f-144">Avec les types génériques, le compilateur est capable d’identifier les incompatibilités de type avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd40f-144">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
- <span data-ttu-id="dd40f-145">**Niveau de performance.**</span><span class="sxs-lookup"><span data-stu-id="dd40f-145">**Performance.**</span></span> <span data-ttu-id="dd40f-146">. Les types génériques ne nécessitent pas de conversion *boxing* et *unboxinging* des données, car chacun d’eux est utilisé pour un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="dd40f-146">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="dd40f-147">Les opérations basées sur `Object` doivent effectuer une conversion boxing des types de données d’entrée pour les convertir en `Object` et effectuer une conversion unboxing des données de sortie.</span><span class="sxs-lookup"><span data-stu-id="dd40f-147">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="dd40f-148">Les conversions boxing et unboxing réduisent les performances.</span><span class="sxs-lookup"><span data-stu-id="dd40f-148">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="dd40f-149">Les types basés sur `Object` sont également à liaison tardive, ce qui signifie que l’accès à leurs membres nécessite du code supplémentaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd40f-149">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="dd40f-150">Cela réduit aussi les performances.</span><span class="sxs-lookup"><span data-stu-id="dd40f-150">This also reduces performance.</span></span>  
  
- <span data-ttu-id="dd40f-151">**Consolidation du code**</span><span class="sxs-lookup"><span data-stu-id="dd40f-151">**Code Consolidation.**</span></span> <span data-ttu-id="dd40f-152">. Le code d’un type générique doit être défini une seule fois.</span><span class="sxs-lookup"><span data-stu-id="dd40f-152">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="dd40f-153">Un ensemble de versions spécifiques au type d’un type de données doit répliquer le même code dans chaque version, la seule différence étant le type de données spécifique à cette version.</span><span class="sxs-lookup"><span data-stu-id="dd40f-153">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="dd40f-154">Avec les types génériques, les versions spécifiques au type sont toutes générées à partir du type générique d’origine.</span><span class="sxs-lookup"><span data-stu-id="dd40f-154">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
- <span data-ttu-id="dd40f-155">**Réutilisation du code**</span><span class="sxs-lookup"><span data-stu-id="dd40f-155">**Code Reuse.**</span></span> <span data-ttu-id="dd40f-156">. S’il est générique, le code qui ne dépend pas d’un type de données particulier peut être réutilisé avec divers types de données.</span><span class="sxs-lookup"><span data-stu-id="dd40f-156">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="dd40f-157">Vous pouvez généralement le réutiliser même avec un type de données que vous n’avez pas prévu initialement.</span><span class="sxs-lookup"><span data-stu-id="dd40f-157">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
- <span data-ttu-id="dd40f-158">**Support de l’IDE**</span><span class="sxs-lookup"><span data-stu-id="dd40f-158">**IDE Support.**</span></span> <span data-ttu-id="dd40f-159">. Quand vous utilisez un type construit déclaré à partir d’un type générique, l’environnement de développement intégré (IDE) peut vous aider pendant le développement de votre code.</span><span class="sxs-lookup"><span data-stu-id="dd40f-159">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="dd40f-160">Par exemple, IntelliSense vous indique les options spécifiques au type disponibles pour un argument d’une méthode ou d’un constructeur.</span><span class="sxs-lookup"><span data-stu-id="dd40f-160">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
- <span data-ttu-id="dd40f-161">**Algorithmes génériques**</span><span class="sxs-lookup"><span data-stu-id="dd40f-161">**Generic Algorithms.**</span></span> <span data-ttu-id="dd40f-162">. Les types génériques sont conseillés pour les algorithmes abstraits qui sont indépendants du type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-162">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="dd40f-163">Par exemple, une procédure générique qui trie des éléments à l’aide de l’interface <xref:System.IComparable> peut être utilisée avec n’importe quel type de données implémentant <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="dd40f-163">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="dd40f-164">Contraintes</span><span class="sxs-lookup"><span data-stu-id="dd40f-164">Constraints</span></span>  

 <span data-ttu-id="dd40f-165">Dans la mesure du possible, le code d’une définition de type générique doit être indépendant du type. Toutefois, vous pouvez avoir besoin d’une fonction agissant sur tous les types de données fournis à votre type générique.</span><span class="sxs-lookup"><span data-stu-id="dd40f-165">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="dd40f-166">Par exemple, si vous voulez comparer deux éléments pour les trier ou les classer, leur type de données doit implémenter l’interface <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="dd40f-166">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="dd40f-167">Vous pouvez appliquer cette exigence en ajoutant une *contrainte* au paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-167">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="dd40f-168">Exemple de contrainte</span><span class="sxs-lookup"><span data-stu-id="dd40f-168">Example of a Constraint</span></span>  

 <span data-ttu-id="dd40f-169">L’exemple suivant présente une définition squelette d’une classe avec une contrainte qui exige que l’argument de type implémente <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="dd40f-169">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="dd40f-170">Si du code tente ensuite de construire une classe de `itemManager` en fournissant un type qui n’implémente pas <xref:System.IComparable>, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="dd40f-170">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="dd40f-171">Types de contraintes</span><span class="sxs-lookup"><span data-stu-id="dd40f-171">Types of Constraints</span></span>  

 <span data-ttu-id="dd40f-172">Une contrainte peut spécifier les exigences suivantes dans n’importe quelle combinaison :</span><span class="sxs-lookup"><span data-stu-id="dd40f-172">Your constraint can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="dd40f-173">L’argument de type doit implémenter une ou plusieurs interfaces</span><span class="sxs-lookup"><span data-stu-id="dd40f-173">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="dd40f-174">L’argument de type doit être du type d’une seule classe (ou hériter de cette classe).</span><span class="sxs-lookup"><span data-stu-id="dd40f-174">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
- <span data-ttu-id="dd40f-175">L’argument de type doit exposer un constructeur sans paramètre, accessible au code qui crée des objets à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="dd40f-175">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
- <span data-ttu-id="dd40f-176">L’argument de type doit être un *type référence*, ou il doit être un *type valeur*</span><span class="sxs-lookup"><span data-stu-id="dd40f-176">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="dd40f-177">Si vous devez spécifier plusieurs contraintes, utilisez une *liste de contraintes* séparée par des virgules et mise entre accolades (`{ }`).</span><span class="sxs-lookup"><span data-stu-id="dd40f-177">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="dd40f-178">Pour exiger un constructeur accessible, vous devez inclure le mot clé [New Operator](../../../language-reference/operators/new-operator.md) dans la liste.</span><span class="sxs-lookup"><span data-stu-id="dd40f-178">To require an accessible constructor, you include the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="dd40f-179">Pour exiger un type référence ou un type valeur, ajoutez le mot clé `Class` ou le mot clé `Structure` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="dd40f-179">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="dd40f-180">Pour plus d’informations sur les contraintes, consultez [Type List](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="dd40f-180">For more information on constraints, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="dd40f-181">Exemple de liste de contraintes</span><span class="sxs-lookup"><span data-stu-id="dd40f-181">Example of Multiple Constraints</span></span>  

 <span data-ttu-id="dd40f-182">L’exemple suivant présente une définition squelette d’une classe générique avec une liste de contraintes sur le paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-182">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="dd40f-183">Dans le code qui crée une instance de cette classe, l’argument de type doit implémenter les deux interfaces <xref:System.IComparable> et <xref:System.IDisposable> , être un type référence et exposer un constructeur sans paramètre accessible.</span><span class="sxs-lookup"><span data-stu-id="dd40f-183">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a><span data-ttu-id="dd40f-184">Termes importants</span><span class="sxs-lookup"><span data-stu-id="dd40f-184">Important Terms</span></span>  

 <span data-ttu-id="dd40f-185">La terminologie suivante s’applique aux types génériques :</span><span class="sxs-lookup"><span data-stu-id="dd40f-185">Generic types introduce and use the following terms:</span></span>  
  
- <span data-ttu-id="dd40f-186">*Type générique*.</span><span class="sxs-lookup"><span data-stu-id="dd40f-186">*Generic Type*.</span></span> <span data-ttu-id="dd40f-187">Définition d’une classe, structure, interface, procédure ou délégué pour laquelle vous fournissez au moins un type de données lors de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="dd40f-187">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
- <span data-ttu-id="dd40f-188">*Paramètre de type*.</span><span class="sxs-lookup"><span data-stu-id="dd40f-188">*Type Parameter*.</span></span> <span data-ttu-id="dd40f-189">Dans une définition de type générique, espace réservé pour un type de données que vous fournissez lors de la déclaration du type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-189">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
- <span data-ttu-id="dd40f-190">*Argument de type*.</span><span class="sxs-lookup"><span data-stu-id="dd40f-190">*Type Argument*.</span></span> <span data-ttu-id="dd40f-191">Type de données spécifique qui remplace un paramètre de type quand vous déclarez un type construit à partir d’un type générique.</span><span class="sxs-lookup"><span data-stu-id="dd40f-191">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
- <span data-ttu-id="dd40f-192">*Contrainte*.</span><span class="sxs-lookup"><span data-stu-id="dd40f-192">*Constraint*.</span></span> <span data-ttu-id="dd40f-193">Condition sur un paramètre de type qui restreint l’argument de type que vous pouvez lui fournir.</span><span class="sxs-lookup"><span data-stu-id="dd40f-193">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="dd40f-194">Une contrainte peut exiger que l’argument de type implémente une interface particulière, soit ou hérite d’une classe particulière, contienne un constructeur sans paramètre accessible, ou soit un type référence ou un type valeur.</span><span class="sxs-lookup"><span data-stu-id="dd40f-194">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="dd40f-195">Vous pouvez combiner ces contraintes, mais vous ne pouvez spécifier qu’une seule classe.</span><span class="sxs-lookup"><span data-stu-id="dd40f-195">You can combine these constraints, but you can specify at most one class.</span></span>  
  
- <span data-ttu-id="dd40f-196">*Type construit*.</span><span class="sxs-lookup"><span data-stu-id="dd40f-196">*Constructed Type*.</span></span> <span data-ttu-id="dd40f-197">Classe, structure, interface, procédure ou délégué déclaré à partir d’un type générique en fournissant des arguments de type pour ses paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="dd40f-197">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd40f-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd40f-198">See also</span></span>

- [<span data-ttu-id="dd40f-199">Data types</span><span class="sxs-lookup"><span data-stu-id="dd40f-199">Data Types</span></span>](index.md)
- [<span data-ttu-id="dd40f-200">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="dd40f-200">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="dd40f-201">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="dd40f-201">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="dd40f-202">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd40f-202">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="dd40f-203">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="dd40f-203">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="dd40f-204">Data types</span><span class="sxs-lookup"><span data-stu-id="dd40f-204">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="dd40f-205">Of</span><span class="sxs-lookup"><span data-stu-id="dd40f-205">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="dd40f-206">Servir</span><span class="sxs-lookup"><span data-stu-id="dd40f-206">As</span></span>](../../../language-reference/statements/as-clause.md)
- [<span data-ttu-id="dd40f-207">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="dd40f-207">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="dd40f-208">Covariance et contravariance</span><span class="sxs-lookup"><span data-stu-id="dd40f-208">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="dd40f-209">Iterators</span><span class="sxs-lookup"><span data-stu-id="dd40f-209">Iterators</span></span>](../../concepts/iterators.md)
