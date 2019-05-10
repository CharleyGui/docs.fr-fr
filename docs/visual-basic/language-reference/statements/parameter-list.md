---
title: Liste de paramètres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: e58d80896d11b4154c7197d4cdaf73a536fdd5e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583549"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="bb6fe-102">Liste de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="bb6fe-103">Spécifie les paramètres de qu'une procédure attend lorsqu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="bb6fe-104">Plusieurs paramètres sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="bb6fe-105">Voici la syntaxe pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6fe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb6fe-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="bb6fe-107">Composants</span><span class="sxs-lookup"><span data-stu-id="bb6fe-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="bb6fe-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-108">Optional.</span></span> <span data-ttu-id="bb6fe-109">Liste des attributs qui s’appliquent à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="bb6fe-110">Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets («`<`« et »`>`»).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="bb6fe-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-111">Optional.</span></span> <span data-ttu-id="bb6fe-112">Spécifie que ce paramètre n’est pas obligatoire lorsque la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="bb6fe-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-113">Optional.</span></span> <span data-ttu-id="bb6fe-114">Spécifie que la procédure ne peut pas remplacer ou réassigner l’élément de variable sous-jacent de l’argument correspondant dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="bb6fe-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-115">Optional.</span></span> <span data-ttu-id="bb6fe-116">Spécifie que la procédure peut modifier l’élément de variable sous-jacent dans le code appelant la même façon que le code d’appel.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="bb6fe-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-117">Optional.</span></span> <span data-ttu-id="bb6fe-118">Spécifie que le dernier paramètre dans la liste de paramètres est un tableau facultatif d’éléments du type de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="bb6fe-119">Cela permet au code appelant de passer un nombre arbitraire d’arguments à la procédure.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="bb6fe-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-120">Required.</span></span> <span data-ttu-id="bb6fe-121">Nom de la variable locale représentant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="bb6fe-122">Obligatoire si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="bb6fe-123">Type de données de la variable locale représentant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="bb6fe-124">Requis pour `Optional` paramètres.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="bb6fe-125">Toute constante ou expression constante qui correspond au type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="bb6fe-126">Si le type est `Object`, ou une classe, interface, tableau ou une structure, la valeur par défaut peut uniquement être `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb6fe-127">Notes</span><span class="sxs-lookup"><span data-stu-id="bb6fe-127">Remarks</span></span>  
 <span data-ttu-id="bb6fe-128">Paramètres sont placés entre parenthèses et séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="bb6fe-129">Un paramètre peut être déclaré avec n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="bb6fe-130">Si vous ne spécifiez pas `parametertype`, les valeurs par défaut `Object`.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="bb6fe-131">Lorsque le code appelant appelle la procédure, il transmet un *argument* à chaque paramètre requis.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="bb6fe-132">Pour plus d’informations, consultez [différences entre les paramètres et Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="bb6fe-133">L’argument que le code appelant passe à chaque paramètre est un pointeur vers un élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="bb6fe-134">Si cet élément est *variable* (une constante, littéral, énumération ou expression), il est impossible pour n’importe quel code pour le modifier.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="bb6fe-135">S’il s’agit une *variable* élément (une variable déclarée, champ, propriété, élément de tableau ou élément de structure), le code appelant peut le modifier.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="bb6fe-136">Pour plus d’informations, consultez [différences entre modifiables et non modifiables Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="bb6fe-137">Si un élément de variable est passé `ByRef`, la procédure peut également le modifier.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="bb6fe-138">Pour plus d’informations, consultez [différences entre passage d’un Argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bb6fe-139">Règles</span><span class="sxs-lookup"><span data-stu-id="bb6fe-139">Rules</span></span>  
  
- <span data-ttu-id="bb6fe-140">**Parenthèses.**</span><span class="sxs-lookup"><span data-stu-id="bb6fe-140">**Parentheses.**</span></span> <span data-ttu-id="bb6fe-141">Si vous spécifiez une liste de paramètres, vous devez le placer entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="bb6fe-142">S’il n’y a aucun paramètre, vous pouvez toujours utiliser des parenthèses entourant une liste vide.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="bb6fe-143">Cela améliore la lisibilité de votre code en clarifiant que l’élément est une procédure.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
- <span data-ttu-id="bb6fe-144">**Paramètres facultatifs.**</span><span class="sxs-lookup"><span data-stu-id="bb6fe-144">**Optional Parameters.**</span></span> <span data-ttu-id="bb6fe-145">Si vous utilisez le `Optional` modificateur sur un paramètre, tous les paramètres suivants dans la liste doivent également être facultatifs et être déclarés à l’aide de la `Optional` modificateur.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="bb6fe-146">Chaque déclaration de paramètre facultatif doit fournir le `defaultvalue` clause.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="bb6fe-147">Pour plus d’informations, consultez [paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
- <span data-ttu-id="bb6fe-148">**Tableaux de paramètres.**</span><span class="sxs-lookup"><span data-stu-id="bb6fe-148">**Parameter Arrays.**</span></span> <span data-ttu-id="bb6fe-149">Vous devez spécifier `ByVal` pour un `ParamArray` paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="bb6fe-150">Vous ne pouvez pas utiliser les deux `Optional` et `ParamArray` dans la même liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="bb6fe-151">Pour plus d’informations, consultez [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
- <span data-ttu-id="bb6fe-152">**Mécanisme de passage.**</span><span class="sxs-lookup"><span data-stu-id="bb6fe-152">**Passing Mechanism.**</span></span> <span data-ttu-id="bb6fe-153">Le mécanisme par défaut pour chaque argument est `ByVal`, ce qui signifie que la procédure ne peut pas modifier l’élément variable sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="bb6fe-154">Toutefois, si l’élément est un type référence, la procédure peut modifier le contenu ou les membres de l’objet sous-jacent, même si elle ne peut pas remplacer ou réassigner l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
- <span data-ttu-id="bb6fe-155">**Noms de paramètre.**</span><span class="sxs-lookup"><span data-stu-id="bb6fe-155">**Parameter Names.**</span></span> <span data-ttu-id="bb6fe-156">Si le type de données du paramètre est un tableau, suivez `parametername` immédiatement par des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="bb6fe-157">Pour plus d’informations sur les noms de paramètre, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bb6fe-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6fe-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb6fe-158">Example</span></span>  
 <span data-ttu-id="bb6fe-159">L’exemple suivant montre un `Function` procédure qui définit deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="bb6fe-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bb6fe-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb6fe-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="bb6fe-161">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="bb6fe-162">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="bb6fe-163">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="bb6fe-164">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="bb6fe-165">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb6fe-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="bb6fe-166">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="bb6fe-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="bb6fe-167">Guide pratique pour diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="bb6fe-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
