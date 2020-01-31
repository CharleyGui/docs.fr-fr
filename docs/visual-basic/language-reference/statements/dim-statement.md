---
title: Dim (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744727"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="2723a-102">Dim, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2723a-102">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="2723a-103">Déclare et alloue de l’espace de stockage pour une ou plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="2723a-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="2723a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2723a-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="2723a-105">Parties</span><span class="sxs-lookup"><span data-stu-id="2723a-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="2723a-106">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-106">Optional.</span></span> <span data-ttu-id="2723a-107">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="2723a-108">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-108">Optional.</span></span> <span data-ttu-id="2723a-109">Il peut s'agir de l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2723a-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="2723a-110">Public</span><span class="sxs-lookup"><span data-stu-id="2723a-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="2723a-111">Protected</span><span class="sxs-lookup"><span data-stu-id="2723a-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="2723a-112">Friend</span><span class="sxs-lookup"><span data-stu-id="2723a-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="2723a-113">Private</span><span class="sxs-lookup"><span data-stu-id="2723a-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="2723a-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2723a-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="2723a-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="2723a-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="2723a-116">Consultez [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="2723a-117">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-117">Optional.</span></span> <span data-ttu-id="2723a-118">Consultez [partagé](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-118">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="2723a-119">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-119">Optional.</span></span> <span data-ttu-id="2723a-120">Consultez [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-120">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="2723a-121">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-121">Optional.</span></span> <span data-ttu-id="2723a-122">Consultez [static](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-122">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="2723a-123">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-123">Optional.</span></span> <span data-ttu-id="2723a-124">Consultez [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-124">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="2723a-125">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-125">Optional.</span></span> <span data-ttu-id="2723a-126">Spécifie qu’il s’agit de variables objets qui font référence à des instances d’une classe qui peuvent déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="2723a-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="2723a-127">Consultez [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-127">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="2723a-128">Requis.</span><span class="sxs-lookup"><span data-stu-id="2723a-128">Required.</span></span> <span data-ttu-id="2723a-129">Liste des variables déclarées dans cette instruction.</span><span class="sxs-lookup"><span data-stu-id="2723a-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="2723a-130">Chaque `variable` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2723a-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="2723a-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="2723a-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="2723a-132">Partie</span><span class="sxs-lookup"><span data-stu-id="2723a-132">Part</span></span>|<span data-ttu-id="2723a-133">Description</span><span class="sxs-lookup"><span data-stu-id="2723a-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="2723a-134">Requis.</span><span class="sxs-lookup"><span data-stu-id="2723a-134">Required.</span></span> <span data-ttu-id="2723a-135">Nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-135">Name of the variable.</span></span> <span data-ttu-id="2723a-136">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="2723a-137">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-137">Optional.</span></span> <span data-ttu-id="2723a-138">Liste des limites de chaque dimension d’une variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="2723a-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="2723a-139">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-139">Optional.</span></span> <span data-ttu-id="2723a-140">Crée une nouvelle instance de la classe lors de l’exécution de l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="2723a-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="2723a-141">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-141">Optional.</span></span> <span data-ttu-id="2723a-142">Type de données de la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="2723a-143">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-143">Optional.</span></span> <span data-ttu-id="2723a-144">Introduit la liste d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="2723a-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="2723a-145">Option facultative.</span><span class="sxs-lookup"><span data-stu-id="2723a-145">Optional.</span></span> <span data-ttu-id="2723a-146">Nom d’une propriété dans la classe à partir de laquelle vous effectuez une instance.</span><span class="sxs-lookup"><span data-stu-id="2723a-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="2723a-147">Obligatoire après `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="2723a-147">Required after `propertyname` =.</span></span> <span data-ttu-id="2723a-148">Expression évaluée et assignée au nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2723a-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="2723a-149">Facultatif si `New` n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="2723a-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="2723a-150">Expression qui est évaluée et assignée à la variable lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="2723a-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2723a-151">Notes</span><span class="sxs-lookup"><span data-stu-id="2723a-151">Remarks</span></span>

<span data-ttu-id="2723a-152">Le compilateur Visual Basic utilise l’instruction `Dim` pour déterminer le type de données de la variable et d’autres informations, telles que le code qui peut accéder à la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="2723a-153">L’exemple suivant déclare une variable qui doit contenir une valeur `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2723a-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="2723a-154">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="2723a-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="2723a-155">Pour un type référence, vous utilisez le mot clé `New` pour créer une nouvelle instance de la classe ou de la structure spécifiée par le type de données.</span><span class="sxs-lookup"><span data-stu-id="2723a-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="2723a-156">Si vous utilisez `New`, vous n’utilisez pas d’expression d’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="2723a-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="2723a-157">Au lieu de cela, vous fournissez des arguments, s’ils sont requis, au constructeur de la classe à partir de laquelle vous créez la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="2723a-158">Vous pouvez déclarer une variable dans une procédure, un bloc, une classe, une structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="2723a-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="2723a-159">Vous ne pouvez pas déclarer une variable dans un fichier source, un espace de noms ou une interface.</span><span class="sxs-lookup"><span data-stu-id="2723a-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="2723a-160">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-160">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="2723a-161">Une variable déclarée au niveau du module, en dehors de toute procédure, est une *variable membre* ou un *champ*.</span><span class="sxs-lookup"><span data-stu-id="2723a-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="2723a-162">Les variables membres sont dans la portée de la classe, de la structure ou du module.</span><span class="sxs-lookup"><span data-stu-id="2723a-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="2723a-163">Une variable déclarée au niveau de la procédure est une *variable locale*.</span><span class="sxs-lookup"><span data-stu-id="2723a-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="2723a-164">Les variables locales se trouvent dans la portée uniquement dans leur procédure ou bloc.</span><span class="sxs-lookup"><span data-stu-id="2723a-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="2723a-165">Les modificateurs d’accès suivants sont utilisés pour déclarer des variables en dehors d’une procédure : `Public`, `Protected`, `Friend`, `Protected Friend`et `Private`.</span><span class="sxs-lookup"><span data-stu-id="2723a-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="2723a-166">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-166">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="2723a-167">Le mot clé `Dim` est facultatif et est généralement omis si vous spécifiez l’un des modificateurs suivants : `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`ou `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="2723a-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="2723a-168">Si `Option Explicit` est activé (valeur par défaut), le compilateur requiert une déclaration pour chaque variable que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="2723a-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="2723a-169">Pour plus d’informations, consultez [Option Explicit, instruction](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-169">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="2723a-170">Spécification d’une valeur initiale</span><span class="sxs-lookup"><span data-stu-id="2723a-170">Specifying an initial value</span></span>

<span data-ttu-id="2723a-171">Vous pouvez assigner une valeur à une variable lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="2723a-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="2723a-172">Pour un type valeur, vous utilisez un *initialiseur* pour fournir une expression à assigner à la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="2723a-173">L’expression doit correspondre à une constante qui peut être calculée au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2723a-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="2723a-174">Si un initialiseur est spécifié et qu’aucun type de données n’est spécifié dans une clause `As`, l' *inférence de type* est utilisée pour déduire le type de données de l’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="2723a-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="2723a-175">Dans l’exemple suivant, les `num1` et `num2` sont fortement typés en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="2723a-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="2723a-176">Dans la deuxième déclaration, l’inférence de type déduit le type de la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="2723a-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="2723a-177">L’inférence de type s’applique au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="2723a-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="2723a-178">Elle ne s’applique pas en dehors d’une procédure dans une classe, une structure, un module ou une interface.</span><span class="sxs-lookup"><span data-stu-id="2723a-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="2723a-179">Pour plus d’informations sur l’inférence de type, consultez [instruction Option Infer](option-infer-statement.md) et [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-179">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="2723a-180">Pour plus d’informations sur ce qui se passe quand un type de données ou un initialiseur n’est pas spécifié, consultez [types de données et valeurs par défaut](dim-statement.md#default) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2723a-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="2723a-181">Vous pouvez utiliser un *initialiseur d’objet* pour déclarer des instances de types nommés et anonymes.</span><span class="sxs-lookup"><span data-stu-id="2723a-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="2723a-182">Le code suivant crée une instance d’une classe `Student` et utilise un initialiseur d’objet pour initialiser les propriétés.</span><span class="sxs-lookup"><span data-stu-id="2723a-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="2723a-183">Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [initialiseurs d’objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), et [types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="2723a-184">Déclaration de plusieurs variables</span><span class="sxs-lookup"><span data-stu-id="2723a-184">Declaring multiple variables</span></span>

<span data-ttu-id="2723a-185">Vous pouvez déclarer plusieurs variables dans une instruction de déclaration, en spécifiant le nom de chaque variable et en suivant les parenthèses de chaque nom de tableau.</span><span class="sxs-lookup"><span data-stu-id="2723a-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="2723a-186">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="2723a-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="2723a-187">Si vous déclarez plusieurs variables avec une seule clause `As`, vous ne pouvez pas fournir un initialiseur pour ce groupe de variables.</span><span class="sxs-lookup"><span data-stu-id="2723a-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="2723a-188">Vous pouvez spécifier des types de données différents pour différentes variables à l’aide d’une clause `As` distincte pour chaque variable que vous déclarez.</span><span class="sxs-lookup"><span data-stu-id="2723a-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="2723a-189">Chaque variable prend le type de données spécifié dans la première clause `As` rencontrée après sa partie `variablename`.</span><span class="sxs-lookup"><span data-stu-id="2723a-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="2723a-190">Tableaux</span><span class="sxs-lookup"><span data-stu-id="2723a-190">Arrays</span></span>

<span data-ttu-id="2723a-191">Vous pouvez déclarer une variable qui contiendra un *tableau*, qui peut contenir plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="2723a-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="2723a-192">Pour spécifier qu’une variable contient un tableau, suivez son `variablename` immédiatement avec des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2723a-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="2723a-193">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-193">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="2723a-194">Vous pouvez spécifier les limites inférieure et supérieure de chaque dimension d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="2723a-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="2723a-195">Pour ce faire, incluez un `boundslist` à l’intérieur des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2723a-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="2723a-196">Pour chaque dimension, le `boundslist` spécifie la limite supérieure et éventuellement la limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="2723a-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="2723a-197">La limite inférieure est toujours égale à zéro, que vous la spécifiiez ou non.</span><span class="sxs-lookup"><span data-stu-id="2723a-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="2723a-198">Chaque index peut varier de zéro à sa valeur limite supérieure.</span><span class="sxs-lookup"><span data-stu-id="2723a-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="2723a-199">Les deux instructions suivantes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="2723a-199">The following two statements are equivalent.</span></span> <span data-ttu-id="2723a-200">Chaque instruction déclare un tableau de 21 `Integer` éléments.</span><span class="sxs-lookup"><span data-stu-id="2723a-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="2723a-201">Lorsque vous accédez au tableau, l’index peut varier de 0 à 20.</span><span class="sxs-lookup"><span data-stu-id="2723a-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="2723a-202">L’instruction suivante déclare un tableau à deux dimensions de type `Double`.</span><span class="sxs-lookup"><span data-stu-id="2723a-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="2723a-203">Le tableau comporte 4 lignes (3 + 1) de 6 colonnes (5 + 1) chacune.</span><span class="sxs-lookup"><span data-stu-id="2723a-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="2723a-204">Notez qu’une limite supérieure représente la valeur la plus élevée possible pour l’index, et non la longueur de la dimension.</span><span class="sxs-lookup"><span data-stu-id="2723a-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="2723a-205">La longueur de la dimension est la limite supérieure plus un.</span><span class="sxs-lookup"><span data-stu-id="2723a-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="2723a-206">Un tableau peut avoir entre 1 et 32 dimensions.</span><span class="sxs-lookup"><span data-stu-id="2723a-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="2723a-207">Vous pouvez laisser toutes les limites vides dans une déclaration de tableau.</span><span class="sxs-lookup"><span data-stu-id="2723a-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="2723a-208">Dans ce cas, le tableau a le nombre de dimensions que vous spécifiez, mais il n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="2723a-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="2723a-209">Elle a la valeur `Nothing` jusqu’à ce que vous initialisez au moins certains de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="2723a-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="2723a-210">L’instruction `Dim` doit spécifier des limites pour toutes les dimensions ou pour aucune dimension.</span><span class="sxs-lookup"><span data-stu-id="2723a-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="2723a-211">Si le tableau a plusieurs dimensions, vous devez inclure des virgules entre les parenthèses pour indiquer le nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="2723a-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="2723a-212">Vous pouvez déclarer un *tableau de longueur zéro* en déclarant l’une des dimensions du tableau avec la valeur-1.</span><span class="sxs-lookup"><span data-stu-id="2723a-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="2723a-213">Une variable qui contient un tableau de longueur zéro n’a pas la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2723a-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="2723a-214">Des tableaux de longueur zéro sont requis par certaines fonctions common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2723a-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="2723a-215">Si vous essayez d’accéder à ce type de tableau, une exception d’exécution se produit.</span><span class="sxs-lookup"><span data-stu-id="2723a-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="2723a-216">Pour plus d’informations, consultez [Tableaux](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-216">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="2723a-217">Vous pouvez initialiser les valeurs d’un tableau à l’aide d’un littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="2723a-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="2723a-218">Pour ce faire, placez les valeurs d’initialisation entre accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="2723a-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="2723a-219">Pour les tableaux multidimensionnels, l’initialisation de chaque dimension séparée est placée entre accolades dans la dimension externe.</span><span class="sxs-lookup"><span data-stu-id="2723a-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="2723a-220">Les éléments sont spécifiés dans l’ordre ligne-principal.</span><span class="sxs-lookup"><span data-stu-id="2723a-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="2723a-221">Pour plus d’informations sur les littéraux de tableau, consultez [tableaux](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-221">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a><span data-ttu-id="2723a-222">Valeurs et types de données par défaut</span><span class="sxs-lookup"><span data-stu-id="2723a-222">Default data types and values</span></span>

<span data-ttu-id="2723a-223">Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="2723a-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="2723a-224">Type de données spécifié ?</span><span class="sxs-lookup"><span data-stu-id="2723a-224">Data type specified?</span></span>|<span data-ttu-id="2723a-225">Initialiseur spécifié ?</span><span class="sxs-lookup"><span data-stu-id="2723a-225">Initializer specified?</span></span>|<span data-ttu-id="2723a-226">Exemple</span><span class="sxs-lookup"><span data-stu-id="2723a-226">Example</span></span>|<span data-ttu-id="2723a-227">Résultat</span><span class="sxs-lookup"><span data-stu-id="2723a-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="2723a-228">Non</span><span class="sxs-lookup"><span data-stu-id="2723a-228">No</span></span>|<span data-ttu-id="2723a-229">Non</span><span class="sxs-lookup"><span data-stu-id="2723a-229">No</span></span>|`Dim qty`|<span data-ttu-id="2723a-230">Si [option strict](option-strict-statement.md) a la valeur OFF (valeur par défaut), la variable est définie sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2723a-230">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="2723a-231">Si `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2723a-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="2723a-232">Non</span><span class="sxs-lookup"><span data-stu-id="2723a-232">No</span></span>|<span data-ttu-id="2723a-233">Oui</span><span class="sxs-lookup"><span data-stu-id="2723a-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="2723a-234">Si [Option Infer](option-infer-statement.md) est activé (valeur par défaut), la variable prend le type de données de l’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="2723a-234">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="2723a-235">Consultez [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-235">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="2723a-236">Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.</span><span class="sxs-lookup"><span data-stu-id="2723a-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="2723a-237">Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2723a-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="2723a-238">Oui</span><span class="sxs-lookup"><span data-stu-id="2723a-238">Yes</span></span>|<span data-ttu-id="2723a-239">Non</span><span class="sxs-lookup"><span data-stu-id="2723a-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="2723a-240">La variable est initialisée avec la valeur par défaut du type de données.</span><span class="sxs-lookup"><span data-stu-id="2723a-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="2723a-241">Consultez le tableau plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="2723a-241">See the table later in this section.</span></span>|
|<span data-ttu-id="2723a-242">Oui</span><span class="sxs-lookup"><span data-stu-id="2723a-242">Yes</span></span>|<span data-ttu-id="2723a-243">Oui</span><span class="sxs-lookup"><span data-stu-id="2723a-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="2723a-244">Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2723a-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="2723a-245">Si vous spécifiez un type de données, mais que vous ne spécifiez pas d’initialiseur, Visual Basic initialise la variable à la valeur par défaut pour son type de données.</span><span class="sxs-lookup"><span data-stu-id="2723a-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="2723a-246">Le tableau suivant indique les valeurs d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="2723a-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="2723a-247">Type de données</span><span class="sxs-lookup"><span data-stu-id="2723a-247">Data type</span></span>|<span data-ttu-id="2723a-248">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="2723a-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="2723a-249">Tous les types numériques (y compris `Byte` et `SByte`)</span><span class="sxs-lookup"><span data-stu-id="2723a-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="2723a-250">0</span><span class="sxs-lookup"><span data-stu-id="2723a-250">0</span></span>|
|`Char`|<span data-ttu-id="2723a-251">Binaire 0</span><span class="sxs-lookup"><span data-stu-id="2723a-251">Binary 0</span></span>|
|<span data-ttu-id="2723a-252">Tous les types référence (y compris `Object`, `String`et tous les tableaux)</span><span class="sxs-lookup"><span data-stu-id="2723a-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="2723a-253">12:00 du 1er janvier de l’année 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="2723a-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="2723a-254">Chaque élément d’une structure est initialisé comme s’il s’agissait d’une variable distincte.</span><span class="sxs-lookup"><span data-stu-id="2723a-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="2723a-255">Si vous déclarez la longueur d’un tableau mais que vous n’initialisez pas ses éléments, chaque élément est initialisé comme s’il s’agissait d’une variable distincte.</span><span class="sxs-lookup"><span data-stu-id="2723a-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="2723a-256">Durée de vie d’une variable locale statique</span><span class="sxs-lookup"><span data-stu-id="2723a-256">Static local variable lifetime</span></span>

<span data-ttu-id="2723a-257">Une variable locale `Static` a une durée de vie plus longue que celle de la procédure dans laquelle elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="2723a-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="2723a-258">Les limites de la durée de vie de la variable dépendent de l’endroit où la procédure est déclarée et si elle est `Shared`.</span><span class="sxs-lookup"><span data-stu-id="2723a-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="2723a-259">Déclaration de procédure</span><span class="sxs-lookup"><span data-stu-id="2723a-259">Procedure declaration</span></span>|<span data-ttu-id="2723a-260">Variable initialisée</span><span class="sxs-lookup"><span data-stu-id="2723a-260">Variable initialized</span></span>|<span data-ttu-id="2723a-261">La variable cesse d’être existante</span><span class="sxs-lookup"><span data-stu-id="2723a-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="2723a-262">Dans un module</span><span class="sxs-lookup"><span data-stu-id="2723a-262">In a module</span></span>|<span data-ttu-id="2723a-263">La première fois que la procédure est appelée</span><span class="sxs-lookup"><span data-stu-id="2723a-263">The first time the procedure is called</span></span>|<span data-ttu-id="2723a-264">Quand votre programme cesse de s’exécuter</span><span class="sxs-lookup"><span data-stu-id="2723a-264">When your program stops execution</span></span>|
|<span data-ttu-id="2723a-265">Dans une classe ou une structure, la procédure est `Shared`</span><span class="sxs-lookup"><span data-stu-id="2723a-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="2723a-266">La première fois que la procédure est appelée sur une instance spécifique ou sur la classe ou la structure elle-même</span><span class="sxs-lookup"><span data-stu-id="2723a-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="2723a-267">Quand votre programme cesse de s’exécuter</span><span class="sxs-lookup"><span data-stu-id="2723a-267">When your program stops execution</span></span>|
|<span data-ttu-id="2723a-268">Dans une classe ou une structure, la procédure n’est pas `Shared`</span><span class="sxs-lookup"><span data-stu-id="2723a-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="2723a-269">La première fois que la procédure est appelée sur une instance spécifique</span><span class="sxs-lookup"><span data-stu-id="2723a-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="2723a-270">Lorsque l’instance est libérée pour garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="2723a-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="2723a-271">Attributs et modificateurs</span><span class="sxs-lookup"><span data-stu-id="2723a-271">Attributes and modifiers</span></span>

<span data-ttu-id="2723a-272">Vous pouvez appliquer des attributs uniquement aux variables membres, et non aux variables locales.</span><span class="sxs-lookup"><span data-stu-id="2723a-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="2723a-273">Un attribut fournit des informations aux métadonnées de l’assembly, ce qui n’est pas significatif pour le stockage temporaire, tel que les variables locales.</span><span class="sxs-lookup"><span data-stu-id="2723a-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="2723a-274">Au niveau du module, vous ne pouvez pas utiliser le modificateur `Static` pour déclarer des variables membres.</span><span class="sxs-lookup"><span data-stu-id="2723a-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="2723a-275">Au niveau de la procédure, vous ne pouvez pas utiliser `Shared`, `Shadows`, `ReadOnly`, `WithEvents`ou n’importe quel modificateur d’accès pour déclarer des variables locales.</span><span class="sxs-lookup"><span data-stu-id="2723a-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="2723a-276">Vous pouvez spécifier le code qui peut accéder à une variable en fournissant une `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="2723a-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="2723a-277">Les variables de membre de classe et de module (en dehors de toute procédure) sont par défaut en accès privé, et les variables de membre de structure ont un accès public par défaut.</span><span class="sxs-lookup"><span data-stu-id="2723a-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="2723a-278">Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="2723a-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="2723a-279">Vous ne pouvez pas utiliser de modificateurs d’accès sur des variables locales (à l’intérieur d’une procédure).</span><span class="sxs-lookup"><span data-stu-id="2723a-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="2723a-280">Vous pouvez spécifier des `WithEvents` uniquement sur des variables membres, et non sur des variables locales à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="2723a-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="2723a-281">Si vous spécifiez `WithEvents`, le type de données de la variable doit être un type de classe spécifique, et non `Object`.</span><span class="sxs-lookup"><span data-stu-id="2723a-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="2723a-282">Vous ne pouvez pas déclarer un tableau avec `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="2723a-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="2723a-283">Pour plus d’informations sur les événements, consultez [événements](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-283">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2723a-284">Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une variable membre avec le nom de la classe, de la structure ou du module.</span><span class="sxs-lookup"><span data-stu-id="2723a-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="2723a-285">Le code en dehors d’une procédure ou d’un bloc ne peut pas faire référence à des variables locales dans cette procédure ou ce bloc.</span><span class="sxs-lookup"><span data-stu-id="2723a-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="2723a-286">Libération des ressources managées</span><span class="sxs-lookup"><span data-stu-id="2723a-286">Releasing managed resources</span></span>

<span data-ttu-id="2723a-287">Le .NET Framework garbage collector supprime les ressources managées sans codage supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="2723a-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="2723a-288">Toutefois, vous pouvez forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="2723a-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="2723a-289">Si une classe contient une ressource particulièrement précieuse et rare (telle qu’une connexion de base de données ou un descripteur de fichier), vous pouvez ne pas vouloir attendre la garbage collection suivante pour nettoyer une instance de classe qui n’est plus utilisée.</span><span class="sxs-lookup"><span data-stu-id="2723a-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="2723a-290">Une classe peut implémenter l’interface <xref:System.IDisposable> pour fournir un moyen de libérer des ressources avant une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2723a-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="2723a-291">Une classe qui implémente cette interface expose une méthode `Dispose` qui peut être appelée pour forcer la libération immédiate de ressources précieuses.</span><span class="sxs-lookup"><span data-stu-id="2723a-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="2723a-292">L’instruction `Using` automatise le processus d’acquisition d’une ressource, d’exécution d’un ensemble d’instructions, puis de suppression de la ressource.</span><span class="sxs-lookup"><span data-stu-id="2723a-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="2723a-293">Toutefois, la ressource doit implémenter l’interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="2723a-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="2723a-294">Pour plus d’informations, consultez [using, instruction](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2723a-294">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="2723a-295">Exemple</span><span class="sxs-lookup"><span data-stu-id="2723a-295">Example</span></span>

<span data-ttu-id="2723a-296">L’exemple suivant déclare des variables à l’aide de l’instruction `Dim` avec diverses options.</span><span class="sxs-lookup"><span data-stu-id="2723a-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="2723a-297">Exemple</span><span class="sxs-lookup"><span data-stu-id="2723a-297">Example</span></span>

<span data-ttu-id="2723a-298">L’exemple suivant répertorie les nombres premiers compris entre 1 et 30.</span><span class="sxs-lookup"><span data-stu-id="2723a-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="2723a-299">La portée des variables locales est décrite dans commentaires de code.</span><span class="sxs-lookup"><span data-stu-id="2723a-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="2723a-300">Exemple</span><span class="sxs-lookup"><span data-stu-id="2723a-300">Example</span></span>

<span data-ttu-id="2723a-301">Dans l’exemple suivant, la variable `speedValue` est déclarée au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="2723a-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="2723a-302">Le mot clé `Private` est utilisé pour déclarer la variable.</span><span class="sxs-lookup"><span data-stu-id="2723a-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="2723a-303">La variable est accessible par n’importe quelle procédure de la classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="2723a-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="2723a-304">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2723a-304">See also</span></span>

- [<span data-ttu-id="2723a-305">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="2723a-305">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="2723a-306">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="2723a-306">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="2723a-307">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="2723a-307">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="2723a-308">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="2723a-308">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="2723a-309">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="2723a-309">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="2723a-310">Page Compiler, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2723a-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="2723a-311">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="2723a-311">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="2723a-312">Tableaux</span><span class="sxs-lookup"><span data-stu-id="2723a-312">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="2723a-313">Initialiseurs d’objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="2723a-313">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="2723a-314">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="2723a-314">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="2723a-315">Initialiseurs d’objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="2723a-315">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="2723a-316">Guide pratique : déclarer un objet à l’aide d’un initialiseur d’objet</span><span class="sxs-lookup"><span data-stu-id="2723a-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="2723a-317">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="2723a-317">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
