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
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582182"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="c7d16-102">Liste de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7d16-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="c7d16-103">Spécifie les paramètres qu’une procédure attend quand elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="c7d16-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="c7d16-104">Plusieurs paramètres sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c7d16-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="c7d16-105">Voici la syntaxe d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7d16-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7d16-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7d16-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="c7d16-107">Composants</span><span class="sxs-lookup"><span data-stu-id="c7d16-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="c7d16-108">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c7d16-108">Optional.</span></span> <span data-ttu-id="c7d16-109">Liste des attributs qui s’appliquent à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7d16-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="c7d16-110">Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus (« `<` » et « `>` »).</span><span class="sxs-lookup"><span data-stu-id="c7d16-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="c7d16-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c7d16-111">Optional.</span></span> <span data-ttu-id="c7d16-112">Spécifie que ce paramètre n’est pas requis lorsque la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="c7d16-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="c7d16-113">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c7d16-113">Optional.</span></span> <span data-ttu-id="c7d16-114">Spécifie que la procédure ne peut pas remplacer ou réassigner l’élément de variable sous-jacent à l’argument correspondant dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="c7d16-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="c7d16-115">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c7d16-115">Optional.</span></span> <span data-ttu-id="c7d16-116">Spécifie que la procédure peut modifier l’élément de variable sous-jacent dans le code appelant de la même façon que le code appelant lui-même.</span><span class="sxs-lookup"><span data-stu-id="c7d16-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="c7d16-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c7d16-117">Optional.</span></span> <span data-ttu-id="c7d16-118">Spécifie que le dernier paramètre de la liste de paramètres est un tableau facultatif d’éléments du type de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="c7d16-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="c7d16-119">Cela permet au code appelant de passer un nombre arbitraire d’arguments à la procédure.</span><span class="sxs-lookup"><span data-stu-id="c7d16-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="c7d16-120">Requis.</span><span class="sxs-lookup"><span data-stu-id="c7d16-120">Required.</span></span> <span data-ttu-id="c7d16-121">Nom de la variable locale représentant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7d16-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="c7d16-122">Obligatoire si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="c7d16-123">Type de données de la variable locale représentant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7d16-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="c7d16-124">Requis pour les paramètres de `Optional`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="c7d16-125">Toute expression constante ou constante qui prend la valeur du type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7d16-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="c7d16-126">Si le type est `Object`, ou une classe, une interface, un tableau ou une structure, la valeur par défaut ne peut être `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7d16-127">Notes</span><span class="sxs-lookup"><span data-stu-id="c7d16-127">Remarks</span></span>

<span data-ttu-id="c7d16-128">Les paramètres sont placés entre parenthèses et séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c7d16-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="c7d16-129">Un paramètre peut être déclaré avec n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="c7d16-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="c7d16-130">Si vous ne spécifiez pas `parametertype`, la valeur par défaut est `Object`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="c7d16-131">Lorsque le code appelant appelle la procédure, il passe un *argument* à chaque paramètre requis.</span><span class="sxs-lookup"><span data-stu-id="c7d16-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="c7d16-132">Pour plus d’informations, consultez [différences entre les paramètres et les arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="c7d16-133">L’argument que le code appelant passe à chaque paramètre est un pointeur vers un élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="c7d16-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="c7d16-134">Si cet élément n’est pas une *variable* (une constante, un littéral, une énumération ou une expression), il est impossible pour un code de le modifier.</span><span class="sxs-lookup"><span data-stu-id="c7d16-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="c7d16-135">S’il s’agit d’un élément *variable* (une variable déclarée, un champ, une propriété, un élément de tableau ou un élément de structure), le code appelant peut le modifier.</span><span class="sxs-lookup"><span data-stu-id="c7d16-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="c7d16-136">Pour plus d’informations, consultez [différences entre les arguments modifiables et non modifiables](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="c7d16-137">Si un élément variable est passé `ByRef`, la procédure peut également le modifier.</span><span class="sxs-lookup"><span data-stu-id="c7d16-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="c7d16-138">Pour plus d’informations, consultez [différences entre le passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="c7d16-139">Règles</span><span class="sxs-lookup"><span data-stu-id="c7d16-139">Rules</span></span>

- <span data-ttu-id="c7d16-140">**Parenthèses.**</span><span class="sxs-lookup"><span data-stu-id="c7d16-140">**Parentheses.**</span></span> <span data-ttu-id="c7d16-141">Si vous spécifiez une liste de paramètres, vous devez la placer entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c7d16-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="c7d16-142">S’il n’y a aucun paramètre, vous pouvez toujours utiliser des parenthèses englobant une liste vide.</span><span class="sxs-lookup"><span data-stu-id="c7d16-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="c7d16-143">Cela améliore la lisibilité de votre code en clarifiant que l’élément est une procédure.</span><span class="sxs-lookup"><span data-stu-id="c7d16-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="c7d16-144">**Paramètres facultatifs.**</span><span class="sxs-lookup"><span data-stu-id="c7d16-144">**Optional Parameters.**</span></span> <span data-ttu-id="c7d16-145">Si vous utilisez le modificateur `Optional` sur un paramètre, tous les paramètres suivants de la liste doivent également être facultatifs et être déclarés à l’aide du modificateur `Optional`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="c7d16-146">Chaque déclaration de paramètre facultative doit fournir la clause `defaultvalue`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="c7d16-147">Pour plus d’informations, consultez [paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="c7d16-148">**Tableaux de paramètres.**</span><span class="sxs-lookup"><span data-stu-id="c7d16-148">**Parameter Arrays.**</span></span> <span data-ttu-id="c7d16-149">Vous devez spécifier `ByVal` pour un paramètre `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="c7d16-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="c7d16-150">Vous ne pouvez pas utiliser à la fois `Optional` et `ParamArray` dans la même liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c7d16-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="c7d16-151">Pour plus d’informations, consultez [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="c7d16-152">**Mécanisme de passage.**</span><span class="sxs-lookup"><span data-stu-id="c7d16-152">**Passing Mechanism.**</span></span> <span data-ttu-id="c7d16-153">Le mécanisme par défaut pour chaque argument est `ByVal`, ce qui signifie que la procédure ne peut pas modifier l’élément de variable sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="c7d16-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="c7d16-154">Toutefois, si l’élément est un type référence, la procédure peut modifier le contenu ou les membres de l’objet sous-jacent, même s’il ne peut pas remplacer ou réassigner l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="c7d16-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="c7d16-155">**Noms de paramètres.**</span><span class="sxs-lookup"><span data-stu-id="c7d16-155">**Parameter Names.**</span></span> <span data-ttu-id="c7d16-156">Si le type de données du paramètre est un tableau, suivez `parametername` immédiatement par des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c7d16-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="c7d16-157">Pour plus d’informations sur les noms de paramètres, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c7d16-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="c7d16-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7d16-158">Example</span></span>

<span data-ttu-id="c7d16-159">L’exemple suivant illustre une procédure `Function` qui définit deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="c7d16-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c7d16-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7d16-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="c7d16-161">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7d16-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c7d16-162">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7d16-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c7d16-163">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7d16-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="c7d16-164">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7d16-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c7d16-165">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7d16-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c7d16-166">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="c7d16-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="c7d16-167">Guide pratique : diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="c7d16-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
