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
ms.openlocfilehash: 59559f8775a5fd66a567897b009272df1727b1e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953330"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="6914a-102">Inférence de type local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6914a-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="6914a-103">Le compilateur Visual Basic utilise l’inférence de *type* pour déterminer les types de données des variables locales `As` déclarées sans clause.</span><span class="sxs-lookup"><span data-stu-id="6914a-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="6914a-104">Le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="6914a-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="6914a-105">Cela vous permet de déclarer des variables sans déclarer explicitement un type, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6914a-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="6914a-106">À la suite des déclarations, `num1` et `num2` sont fortement typées en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="6914a-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
> <span data-ttu-id="6914a-107">Si vous ne `num2` souhaitez pas que dans l’exemple précédent soit tapé comme un `Integer`, vous pouvez spécifier un autre type à l’aide d’une déclaration comme `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="6914a-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
> <span data-ttu-id="6914a-108">L’inférence de type ne peut être utilisée que pour les variables locales non statiques; elle ne peut pas être utilisée pour déterminer le type des champs de classe, des propriétés ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="6914a-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="6914a-109">L’inférence de type local s’applique au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="6914a-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="6914a-110">Elle ne peut pas être utilisée pour déclarer des variables au niveau du module (dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc).</span><span class="sxs-lookup"><span data-stu-id="6914a-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="6914a-111">Si `num2` , dans l’exemple précédent, était un champ d’une classe au lieu d’une variable locale dans une procédure, la déclaration provoquerait `Option Strict` une erreur avec on `Object` et `num2` classifierait comme `Option Strict` with OFF.</span><span class="sxs-lookup"><span data-stu-id="6914a-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="6914a-112">De même, l’inférence de type local ne s’applique pas aux variables de `Static`niveau procédure déclarées comme.</span><span class="sxs-lookup"><span data-stu-id="6914a-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="6914a-113">Inférence de type et Liaison tardive</span><span class="sxs-lookup"><span data-stu-id="6914a-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="6914a-114">Le code qui utilise l’inférence de type ressemble au code qui s’appuie sur la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="6914a-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="6914a-115">Toutefois, l’inférence de type type fortement la variable au lieu de `Object`la laisser en tant que.</span><span class="sxs-lookup"><span data-stu-id="6914a-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="6914a-116">Le compilateur utilise l’initialiseur d’une variable pour déterminer le type de la variable au moment de la compilation pour produire du code à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="6914a-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="6914a-117">Dans l’exemple précédent, `num2`, comme `num1` `Integer`, est de type.</span><span class="sxs-lookup"><span data-stu-id="6914a-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="6914a-118">Le comportement des variables à liaison anticipée diffère de celui des variables à liaison tardive, pour lesquelles le type est connu uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6914a-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="6914a-119">La connaissance du type le plus tôt permet au compilateur d’identifier les problèmes avant leur exécution, d’allouer de la mémoire avec précision et d’effectuer d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="6914a-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="6914a-120">La liaison précoce permet également au Visual Basic environnement de développement intégré (IDE) de fournir une aide IntelliSense sur les membres d’un objet.</span><span class="sxs-lookup"><span data-stu-id="6914a-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="6914a-121">La liaison précoce est également préférable pour les performances.</span><span class="sxs-lookup"><span data-stu-id="6914a-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="6914a-122">Cela est dû au fait que toutes les données stockées dans une variable à liaison tardive doivent `Object`être encapsulées en tant que type et que l’accès aux membres du type au moment de l’exécution rend le programme plus lent.</span><span class="sxs-lookup"><span data-stu-id="6914a-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6914a-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="6914a-123">Examples</span></span>  
 <span data-ttu-id="6914a-124">L’inférence de type se produit lorsqu’une variable locale est `As` déclarée sans clause et initialisée.</span><span class="sxs-lookup"><span data-stu-id="6914a-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="6914a-125">Le compilateur utilise le type de la valeur initiale affectée comme type de la variable.</span><span class="sxs-lookup"><span data-stu-id="6914a-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="6914a-126">Par exemple, chacune des lignes de code suivantes déclare une variable de type `String`.</span><span class="sxs-lookup"><span data-stu-id="6914a-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="6914a-127">Le code suivant illustre deux façons équivalentes de créer un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="6914a-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="6914a-128">Il est pratique d’utiliser l’inférence de type pour déterminer le type d’une variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="6914a-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="6914a-129">Dans le code suivant, le compilateur déduit que `number` est un `Integer` , car `someNumbers2` dans l’exemple précédent, il s’agit d’un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="6914a-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="6914a-130">L’inférence de type local peut être `Using` utilisée dans les instructions pour établir le type du nom de la ressource, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6914a-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="6914a-131">Le type d’une variable peut également être déduit à partir des valeurs de retour des fonctions, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6914a-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="6914a-132">Et sont des tableaux de processus, car `Process.GetProcesses` retourne un tableau de processus. `pList2` `pList1`</span><span class="sxs-lookup"><span data-stu-id="6914a-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="6914a-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="6914a-133">Option Infer</span></span>  
 <span data-ttu-id="6914a-134">`Option Infer`vous permet de spécifier si l’inférence de type local est autorisée dans un fichier particulier.</span><span class="sxs-lookup"><span data-stu-id="6914a-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="6914a-135">Pour activer ou bloquer l’option, tapez l’une des instructions suivantes au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="6914a-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="6914a-136">Si vous ne spécifiez pas de valeur `Option Infer` pour dans votre code, la valeur par `Option Infer On`défaut du compilateur est.</span><span class="sxs-lookup"><span data-stu-id="6914a-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> 
  
 <span data-ttu-id="6914a-137">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="6914a-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="6914a-138">Pour plus d’informations, consultez [instruction Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [page compiler, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6914a-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6914a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6914a-139">See also</span></span>

- [<span data-ttu-id="6914a-140">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="6914a-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="6914a-141">Liaison anticipée et liaison tardive</span><span class="sxs-lookup"><span data-stu-id="6914a-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="6914a-142">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="6914a-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="6914a-143">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="6914a-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="6914a-144">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="6914a-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="6914a-145">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="6914a-145">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="6914a-146">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6914a-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
