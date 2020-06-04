---
title: Caractères spéciaux dans le code
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: c9b170ed812474cdeee100f1dc388d5c7e85f2cc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400589"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="125dc-102">Caractères spéciaux dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="125dc-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="125dc-103">Parfois, vous devez utiliser des caractères spéciaux dans votre code, autrement dit, des caractères qui ne sont pas alphabétiques ou numériques.</span><span class="sxs-lookup"><span data-stu-id="125dc-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="125dc-104">La ponctuation et les caractères spéciaux du jeu de caractères Visual Basic ont plusieurs utilisations, de l’organisation du texte de programme à la définition des tâches exécutées par le compilateur ou le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="125dc-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="125dc-105">Ils ne spécifient pas d'opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="125dc-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="125dc-106">Parenthèses</span><span class="sxs-lookup"><span data-stu-id="125dc-106">Parentheses</span></span>  
 <span data-ttu-id="125dc-107">Utilisez des parenthèses lorsque vous définissez une procédure, telle que `Sub` ou `Function` .</span><span class="sxs-lookup"><span data-stu-id="125dc-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="125dc-108">Vous devez placer toutes les listes d’arguments de procédure entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="125dc-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="125dc-109">Vous utilisez également des parenthèses pour placer des variables ou des arguments dans des groupes logiques, en particulier pour remplacer l’ordre de priorité par défaut des opérateurs dans une expression complexe.</span><span class="sxs-lookup"><span data-stu-id="125dc-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="125dc-110">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="125dc-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="125dc-111">Après l’exécution du code précédent, la valeur de `d` est 8,225 et la valeur de `e` est 3.</span><span class="sxs-lookup"><span data-stu-id="125dc-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="125dc-112">Le calcul pour `d` utilise la priorité par défaut de `/` sur `+` et équivaut à `d = b + (c / a)` .</span><span class="sxs-lookup"><span data-stu-id="125dc-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="125dc-113">Les parenthèses dans le calcul de `e` remplacent la priorité par défaut.</span><span class="sxs-lookup"><span data-stu-id="125dc-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="125dc-114">Séparateurs</span><span class="sxs-lookup"><span data-stu-id="125dc-114">Separators</span></span>  
 <span data-ttu-id="125dc-115">Les séparateurs effectuent ce que leur nom suggère : ils séparent des sections de code.</span><span class="sxs-lookup"><span data-stu-id="125dc-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="125dc-116">Dans Visual Basic, le caractère de séparation est le signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="125dc-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="125dc-117">Utilisez des séparateurs lorsque vous souhaitez inclure plusieurs instructions sur une seule ligne plutôt que des lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="125dc-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="125dc-118">Cela permet d’économiser de l’espace et d’améliorer la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="125dc-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="125dc-119">L’exemple suivant montre trois instructions séparées par des signes deux-points.</span><span class="sxs-lookup"><span data-stu-id="125dc-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="125dc-120">Pour plus d’informations, consultez [Comment : arrêter et combiner des instructions dans le code](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="125dc-120">For more information, see [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="125dc-121">Le caractère deux-points ( `:` ) est également utilisé pour identifier une étiquette d’instruction.</span><span class="sxs-lookup"><span data-stu-id="125dc-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="125dc-122">Pour plus d’informations, consultez [Comment : étiqueter des instructions](how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="125dc-122">For more information, see [How to: Label Statements](how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="125dc-123">Concaténation</span><span class="sxs-lookup"><span data-stu-id="125dc-123">Concatenation</span></span>  
 <span data-ttu-id="125dc-124">Utilisez l' `&` opérateur pour la *concaténation*ou la liaison de chaînes.</span><span class="sxs-lookup"><span data-stu-id="125dc-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="125dc-125">Ne confondez pas l’opérateur avec l' `+` opérateur, qui additionne les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="125dc-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="125dc-126">Si vous utilisez l' `+` opérateur pour concaténer lorsque vous travaillez sur des valeurs numériques, vous pouvez obtenir des résultats incorrects.</span><span class="sxs-lookup"><span data-stu-id="125dc-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="125dc-127">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="125dc-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="125dc-128">Après l’exécution du code précédent, la valeur de `resultA` est 21,01 et la valeur de `resultB` est « 10,0111 ».</span><span class="sxs-lookup"><span data-stu-id="125dc-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="125dc-129">Opérateurs d’accès aux membres</span><span class="sxs-lookup"><span data-stu-id="125dc-129">Member Access Operators</span></span>  
 <span data-ttu-id="125dc-130">Pour accéder à un membre d’un type, vous utilisez l’opérateur point ( `.` ) ou point d’exclamation ( `!` ) entre le nom de type et le nom de membre.</span><span class="sxs-lookup"><span data-stu-id="125dc-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="125dc-131">Point (.) And</span><span class="sxs-lookup"><span data-stu-id="125dc-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="125dc-132">Utilisez l' `.` opérateur sur une classe, une structure, une interface ou une énumération en tant qu’opérateur d’accès aux membres.</span><span class="sxs-lookup"><span data-stu-id="125dc-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="125dc-133">Le membre peut être un champ, une propriété, un événement ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="125dc-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="125dc-134">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="125dc-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="125dc-135">Point d’exclamation ( !) And</span><span class="sxs-lookup"><span data-stu-id="125dc-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="125dc-136">Utilisez l' `!` opérateur uniquement sur une classe ou une interface comme opérateur d’accès au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="125dc-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="125dc-137">La classe ou l’interface doit avoir une propriété par défaut qui accepte un seul `String` argument.</span><span class="sxs-lookup"><span data-stu-id="125dc-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="125dc-138">L’identificateur qui suit immédiatement l' `!` opérateur devient la valeur d’argument passée à la propriété par défaut sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="125dc-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="125dc-139">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="125dc-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="125dc-140">Les trois lignes de sortie de `MsgBox` tous affichent la valeur `32856` .</span><span class="sxs-lookup"><span data-stu-id="125dc-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="125dc-141">La première ligne utilise l’accès traditionnel à la propriété `index` , la seconde utilise le fait qu’il `index` s’agit de la propriété par défaut de la classe `hasDefault` , et la troisième utilise l’accès au dictionnaire pour la classe.</span><span class="sxs-lookup"><span data-stu-id="125dc-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="125dc-142">Notez que le deuxième opérande de l' `!` opérateur doit être un identificateur de Visual Basic valide qui n’est pas placé entre guillemets doubles ( `" "` ).</span><span class="sxs-lookup"><span data-stu-id="125dc-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="125dc-143">En d’autres termes, vous ne pouvez pas utiliser un littéral de chaîne ou une variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="125dc-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="125dc-144">La modification suivante apportée à la dernière ligne de l' `MsgBox` appel génère une erreur, car `"X"` est un littéral de chaîne délimité.</span><span class="sxs-lookup"><span data-stu-id="125dc-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="125dc-145">Les références aux collections par défaut doivent être explicites.</span><span class="sxs-lookup"><span data-stu-id="125dc-145">References to default collections must be explicit.</span></span> <span data-ttu-id="125dc-146">En particulier, vous ne pouvez pas utiliser l' `!` opérateur sur une variable à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="125dc-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="125dc-147">Le `!` caractère est également utilisé comme `Single` caractère de type.</span><span class="sxs-lookup"><span data-stu-id="125dc-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125dc-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="125dc-148">See also</span></span>

- [<span data-ttu-id="125dc-149">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="125dc-149">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="125dc-150">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="125dc-150">Type Characters</span></span>](../language-features/data-types/type-characters.md)
