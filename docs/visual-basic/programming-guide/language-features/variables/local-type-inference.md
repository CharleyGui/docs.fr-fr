---
title: Inférence de type local (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 786466cb0b94a96e629a1f173388ed7d40be7256
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661919"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="cd9d6-102">Inférence de type local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd9d6-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="cd9d6-103">Le compilateur Visual Basic utilise *l’inférence de type* pour déterminer les types de données des variables locales déclarées sans un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="cd9d6-104">Le compilateur déduit le type de la variable du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="cd9d6-105">Cela vous permet de déclarer des variables sans déclarer explicitement un type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="cd9d6-106">À la suite les déclarations, les deux `num1` et `num2` sont fortement typées en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="cd9d6-107">Si vous ne souhaitez pas `num2` dans l’exemple précédent soit typée comme un `Integer`, vous pouvez spécifier un autre type à l’aide d’une déclaration telle que `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="cd9d6-108">Inférence de type peut être utilisée uniquement pour les variables locales non statiques ; Il ne peut pas être utilisé pour déterminer le type des champs de classe, des propriétés ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="cd9d6-109">Inférence de type local s’applique au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="cd9d6-110">Il ne peut pas être utilisé pour déclarer des variables au niveau du module (au sein d’une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc).</span><span class="sxs-lookup"><span data-stu-id="cd9d6-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="cd9d6-111">Si `num2` dans l’exemple précédent ont un champ d’une classe au lieu d’une variable locale dans une procédure, la déclaration génère une erreur avec `Option Strict` et classifieriez `num2` comme un `Object` avec `Option Strict` désactivé.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="cd9d6-112">De même, l’inférence de type local ne s’applique pas aux variables de niveau procédure déclarées en tant que `Static`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="cd9d6-113">Visual Studio l’inférence de type. La liaison tardive</span><span class="sxs-lookup"><span data-stu-id="cd9d6-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="cd9d6-114">Code utilise l’inférence de type ressemble au code qui s’appuie sur la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="cd9d6-115">Toutefois, l’inférence de type type fort à la variable au lieu de laisser en tant que `Object`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="cd9d6-116">Le compilateur utilise l’initialiseur de variable pour déterminer le type de variable au moment de la compilation pour produire un code à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="cd9d6-117">Dans l’exemple précédent, `num2`, comme `num1`, est typé comme un `Integer`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="cd9d6-118">Le comportement des variables à liaison anticipée diffère de celui des variables à liaison tardive, dont le type est connu uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="cd9d6-119">Connaître le type tôt permet au compilateur d’identifier les problèmes avant l’exécution, d’allouer la mémoire précisément et d’effectuer d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="cd9d6-120">Liaison anticipée permet également de l’environnement de développement intégré (IDE) pour fournir une aide IntelliSense sur les membres d’un objet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="cd9d6-121">Liaison anticipée est également par défaut pour les performances.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="cd9d6-122">Il s’agit, car toutes les données stockées dans une variable à liaison tardive doivent être encapsulées en tant que type `Object`, ainsi que l’accès aux membres du type au moment de l’exécution ralentit le programme.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cd9d6-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="cd9d6-123">Examples</span></span>  
 <span data-ttu-id="cd9d6-124">Inférence de type se produit lorsqu’une variable locale est déclarée sans un `As` clause et initialisé.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="cd9d6-125">Le compilateur utilise le type de la valeur initiale assignée en tant que le type de la variable.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="cd9d6-126">Par exemple, chacune des lignes de code suivants déclare une variable de type `String`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="cd9d6-127">Le code suivant illustre deux méthodes pour créer un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="cd9d6-128">Il est pratique d’utiliser l’inférence de type pour déterminer le type d’une variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="cd9d6-129">Dans le code suivant, le compilateur déduit que `number` est un `Integer` car `someNumbers2` à partir de l’exemple précédent est un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="cd9d6-130">Inférence de type local peut être utilisé dans `Using` instructions pour établir le type de nom de la ressource, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="cd9d6-131">Le type d’une variable peut également être déduit à partir de valeurs de retour des fonctions, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="cd9d6-132">Les deux `pList1` et `pList2` sont des tableaux de processus, car `Process.GetProcesses` retourne un tableau de processus.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="cd9d6-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="cd9d6-133">Option Infer</span></span>  
 <span data-ttu-id="cd9d6-134">`Option Infer` vous permet de que spécifier si l’inférence de type local est autorisée dans un fichier particulier.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="cd9d6-135">Pour activer ou bloquer l’option, tapez une des instructions suivantes au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="cd9d6-136">Si vous ne spécifiez pas une valeur pour `Option Infer` dans votre code, la valeur par défaut du compilateur est `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> 
  
 <span data-ttu-id="cd9d6-137">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="cd9d6-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="cd9d6-138">Pour plus d’informations, consultez [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cd9d6-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9d6-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd9d6-139">See also</span></span>

- [<span data-ttu-id="cd9d6-140">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="cd9d6-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="cd9d6-141">Liaison anticipée et liaison tardive</span><span class="sxs-lookup"><span data-stu-id="cd9d6-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="cd9d6-142">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="cd9d6-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="cd9d6-143">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="cd9d6-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="cd9d6-144">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="cd9d6-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="cd9d6-145">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="cd9d6-145">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="cd9d6-146">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd9d6-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
