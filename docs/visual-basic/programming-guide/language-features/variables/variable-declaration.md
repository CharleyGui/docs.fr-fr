---
title: Déclaration de variable
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 8d78509e1604fee4a151608f6166de6fc8ccfdaa
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080151"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="63625-102">Déclaration de variable en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63625-102">Variable Declaration in Visual Basic</span></span>

<span data-ttu-id="63625-103">Vous déclarez une variable pour spécifier son nom et ses caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="63625-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="63625-104">L’instruction de déclaration pour les variables est l' [instruction Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="63625-104">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="63625-105">Son emplacement et son contenu déterminent les caractéristiques de la variable.</span><span class="sxs-lookup"><span data-stu-id="63625-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="63625-106">Pour connaître les règles et les considérations relatives au nommage des variables, consultez [noms d’éléments déclarés](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="63625-106">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="63625-107">Niveaux de déclaration</span><span class="sxs-lookup"><span data-stu-id="63625-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="63625-108">Variables locales et de membre</span><span class="sxs-lookup"><span data-stu-id="63625-108">Local and Member Variables</span></span>  

 <span data-ttu-id="63625-109">Une *variable locale* est une variable déclarée dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="63625-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="63625-110">Une *variable membre* est un membre d’un type Visual Basic ; elle est déclarée au niveau du module, à l’intérieur d’une classe, d’une structure ou d’un module, mais pas dans une procédure interne à cette classe, structure ou module.</span><span class="sxs-lookup"><span data-stu-id="63625-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="63625-111">Variables partagées et d’instance</span><span class="sxs-lookup"><span data-stu-id="63625-111">Shared and Instance Variables</span></span>  

 <span data-ttu-id="63625-112">Dans une classe ou une structure, la catégorie d’une variable membre varie selon qu’elle est partagée ou non.</span><span class="sxs-lookup"><span data-stu-id="63625-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="63625-113">S’il est déclaré avec le mot clé [Shared](../../../language-reference/modifiers/shared.md) , il s’agit d’une *variable partagée*, qui existe dans une seule copie partagée entre toutes les instances de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="63625-113">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="63625-114">Dans le cas contraire, il s’agit d’une *variable d’instance*, et une copie distincte de celle-ci est créée pour chaque instance de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="63625-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="63625-115">Une copie donnée d’une variable d’instance est disponible uniquement pour l’instance de la classe ou de la structure dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="63625-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="63625-116">Elle est indépendante d’une copie de la variable d’instance dans une autre instance de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="63625-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="63625-117">Déclaration du type de données</span><span class="sxs-lookup"><span data-stu-id="63625-117">Declaring Data Type</span></span>  

 <span data-ttu-id="63625-118">La clause [As](../../../language-reference/statements/as-clause.md) dans l’instruction de déclaration vous permet de définir le type de données ou le type d’objet de la variable que vous déclarez.</span><span class="sxs-lookup"><span data-stu-id="63625-118">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="63625-119">Vous pouvez spécifier l’un des types suivants pour une variable :</span><span class="sxs-lookup"><span data-stu-id="63625-119">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="63625-120">Type de données élémentaire, tel que `Boolean` , `Long` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="63625-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="63625-121">Type de données composite, tel qu’un tableau ou une structure</span><span class="sxs-lookup"><span data-stu-id="63625-121">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="63625-122">Un type d’objet, ou classe, défini dans votre application ou dans une autre application</span><span class="sxs-lookup"><span data-stu-id="63625-122">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="63625-123">Une classe .NET Framework, telle que <xref:System.Windows.Forms.Label> ou <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="63625-123">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="63625-124">Type d’interface, tel que <xref:System.IComparable> ou <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="63625-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="63625-125">Vous pouvez déclarer plusieurs variables dans une instruction sans avoir à répéter le type de données.</span><span class="sxs-lookup"><span data-stu-id="63625-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="63625-126">Dans les instructions suivantes, les variables `i` , `j` et `k` sont déclarées en tant que type `Integer` , `l` et sous la forme `m` , et `Long` `x` et `y` comme `Single` suit :</span><span class="sxs-lookup"><span data-stu-id="63625-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="63625-127">Pour plus d’informations sur les types de données, consultez [types de données](../data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="63625-127">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="63625-128">Pour plus d’informations sur les objets, consultez [objets et classes](../objects-and-classes/index.md) et [programmation à l’aide de composants](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="63625-128">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="63625-129">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="63625-129">Local Type Inference</span></span>  

 <span data-ttu-id="63625-130">L' *inférence de type* est utilisée pour déterminer les types de données des variables locales déclarées sans `As` clause.</span><span class="sxs-lookup"><span data-stu-id="63625-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="63625-131">Le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="63625-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="63625-132">Cela vous permet de déclarer des variables sans déclarer explicitement un type.</span><span class="sxs-lookup"><span data-stu-id="63625-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="63625-133">Dans l’exemple suivant, `num1` et `num2` sont fortement typés en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="63625-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="63625-134">Si vous souhaitez utiliser l’inférence de type local, `Option Infer` doit avoir la valeur `On` .</span><span class="sxs-lookup"><span data-stu-id="63625-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="63625-135">Pour plus d’informations, consultez [Inférence de type de variable locale](local-type-inference.md) et [Option Infer, instruction](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="63625-135">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="63625-136">Caractéristiques des variables déclarées</span><span class="sxs-lookup"><span data-stu-id="63625-136">Characteristics of Declared Variables</span></span>  

 <span data-ttu-id="63625-137">La durée de *vie* d’une variable est la période pendant laquelle elle peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="63625-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="63625-138">En général, une variable existe tant que l’élément qui la déclare (telle qu’une procédure ou une classe) continue à exister.</span><span class="sxs-lookup"><span data-stu-id="63625-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="63625-139">Si la variable n’a pas besoin de continuer à s’exécuter au-delà de la durée de vie de son élément conteneur, vous n’avez rien à faire particulier dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="63625-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="63625-140">Si la variable doit continuer à exister plus longtemps que son élément conteneur, vous pouvez inclure le `Static` `Shared` mot clé ou dans son `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="63625-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="63625-141">Pour plus d’informations, consultez [durée de vie dans Visual Basic](../declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="63625-141">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="63625-142">La *portée* d’une variable est l’ensemble du code qui peut y faire référence sans qualifier son nom.</span><span class="sxs-lookup"><span data-stu-id="63625-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="63625-143">L’étendue d’une variable est déterminée par l’emplacement où elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="63625-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="63625-144">Le code situé dans une région donnée peut utiliser les variables définies dans cette région sans avoir à qualifier leurs noms.</span><span class="sxs-lookup"><span data-stu-id="63625-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="63625-145">Pour plus d'informations, consultez [Scope in Visual Basic](../declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="63625-145">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="63625-146">Le niveau d' *accès* d’une variable est l’étendue du code qui a l’autorisation d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="63625-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="63625-147">Cela est déterminé par le modificateur d’accès (par exemple, [public](../../../language-reference/modifiers/public.md) ou [privé](../../../language-reference/modifiers/private.md)) que vous utilisez dans l' `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="63625-147">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="63625-148">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="63625-148">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63625-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63625-149">See also</span></span>

- [<span data-ttu-id="63625-150">Comment : créer une variable</span><span class="sxs-lookup"><span data-stu-id="63625-150">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="63625-151">Comment : placer des données dans et en dehors d'une variable</span><span class="sxs-lookup"><span data-stu-id="63625-151">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="63625-152">Data types</span><span class="sxs-lookup"><span data-stu-id="63625-152">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="63625-153">Protect</span><span class="sxs-lookup"><span data-stu-id="63625-153">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="63625-154">Friend</span><span class="sxs-lookup"><span data-stu-id="63625-154">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="63625-155">Statique</span><span class="sxs-lookup"><span data-stu-id="63625-155">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="63625-156">Caractéristiques des éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="63625-156">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="63625-157">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="63625-157">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="63625-158">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="63625-158">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
