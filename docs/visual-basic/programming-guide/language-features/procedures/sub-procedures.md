---
title: procédures Sub
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163811"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="65371-102">Procédures Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65371-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="65371-103">Une procédure `Sub` est une série d’instructions Visual Basic délimitée par les instructions `Sub` et `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="65371-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="65371-104">La procédure `Sub` effectue une tâche, puis retourne le contrôle au code appelant, mais elle ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="65371-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="65371-105">Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après l’instruction `Sub` et en se terminant par la première instruction `End Sub`, `Exit Sub`ou `Return` rencontrée.</span><span class="sxs-lookup"><span data-stu-id="65371-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="65371-106">Vous pouvez définir une procédure `Sub` dans des modules, des classes et des structures.</span><span class="sxs-lookup"><span data-stu-id="65371-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="65371-107">Par défaut, il s’agit de `Public`, ce qui signifie que vous pouvez l’appeler à partir de n’importe quel endroit de votre application ayant accès au module, à la classe ou à la structure dans laquelle vous l’avez défini.</span><span class="sxs-lookup"><span data-stu-id="65371-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="65371-108">La *méthode* term décrit une `Sub` ou `Function` procédure accessible à partir de l’extérieur de son module, de sa classe ou de sa structure de définition.</span><span class="sxs-lookup"><span data-stu-id="65371-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="65371-109">Pour plus d’informations, consultez [Procédures](./index.md).</span><span class="sxs-lookup"><span data-stu-id="65371-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="65371-110">Une procédure `Sub` peut prendre des arguments, tels que des constantes, des variables ou des expressions, qui lui sont passés par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="65371-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="65371-111">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="65371-111">Declaration syntax</span></span>

<span data-ttu-id="65371-112">La syntaxe de la déclaration d’une procédure `Sub` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="65371-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="65371-113">La `modifiers` peut spécifier le niveau d’accès et des informations sur la surcharge, le remplacement, le partage et l’occultation.</span><span class="sxs-lookup"><span data-stu-id="65371-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="65371-114">Pour plus d’informations, consultez [Sub, instruction](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="65371-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="65371-115">Déclaration de paramètre</span><span class="sxs-lookup"><span data-stu-id="65371-115">Parameter declaration</span></span>

<span data-ttu-id="65371-116">Vous pouvez déclarer chaque paramètre de procédure de la même façon que vous déclarez une variable, en spécifiant le nom du paramètre et le type de données.</span><span class="sxs-lookup"><span data-stu-id="65371-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="65371-117">Vous pouvez également spécifier le mécanisme de passage, et si le paramètre est facultatif ou un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="65371-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="65371-118">La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :</span><span class="sxs-lookup"><span data-stu-id="65371-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="65371-119">Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="65371-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="65371-120">La syntaxe permettant de spécifier une valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="65371-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="65371-121">Paramètres en tant que variables locales</span><span class="sxs-lookup"><span data-stu-id="65371-121">Parameters as local variables</span></span>

<span data-ttu-id="65371-122">Lorsque le contrôle passe à la procédure, chaque paramètre est traité comme une variable locale.</span><span class="sxs-lookup"><span data-stu-id="65371-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="65371-123">Cela signifie que sa durée de vie est la même que celle de la procédure, et que son étendue est l’ensemble de la procédure.</span><span class="sxs-lookup"><span data-stu-id="65371-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="65371-124">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="65371-124">Calling syntax</span></span>

<span data-ttu-id="65371-125">Vous appelez explicitement une procédure `Sub` à l’aide d’une instruction d’appel autonome.</span><span class="sxs-lookup"><span data-stu-id="65371-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="65371-126">Vous ne pouvez pas l’appeler en utilisant son nom dans une expression.</span><span class="sxs-lookup"><span data-stu-id="65371-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="65371-127">Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="65371-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="65371-128">Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="65371-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="65371-129">L’utilisation du mot clé `Call` est facultative, mais n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="65371-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="65371-130">La syntaxe d’un appel à une procédure `Sub` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="65371-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="65371-131">Vous pouvez appeler une méthode `Sub` à partir de l’extérieur de la classe qui la définit.</span><span class="sxs-lookup"><span data-stu-id="65371-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="65371-132">Tout d’abord, vous devez utiliser le mot clé `New` pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="65371-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="65371-133">Pour plus d’informations, consultez [New, opérateur](../../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="65371-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="65371-134">Ensuite, vous pouvez utiliser la syntaxe suivante pour appeler la méthode `Sub` sur l’objet d’instance :</span><span class="sxs-lookup"><span data-stu-id="65371-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="65371-135">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="65371-135">Illustration of declaration and call</span></span>

<span data-ttu-id="65371-136">La procédure `Sub` suivante indique à l’opérateur d’ordinateur quelle tâche l’application est sur le point d’effectuer, et affiche également un horodatage.</span><span class="sxs-lookup"><span data-stu-id="65371-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="65371-137">Au lieu de dupliquer ce code au début de chaque tâche, l’application appelle simplement `tellOperator` à partir de différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="65371-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="65371-138">Chaque appel passe une chaîne dans l’argument `task` qui identifie la tâche en cours de démarrage.</span><span class="sxs-lookup"><span data-stu-id="65371-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="65371-139">L’exemple suivant montre un appel typique à `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="65371-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="65371-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65371-140">See also</span></span>

- [<span data-ttu-id="65371-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="65371-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="65371-142">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="65371-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="65371-143">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="65371-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="65371-144">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="65371-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="65371-145">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="65371-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="65371-146">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="65371-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="65371-147">Guide pratique : appeler une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="65371-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="65371-148">Comment : appeler un gestionnaire d’événements dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65371-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
