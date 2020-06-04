---
title: 'Comment : faire correspondre une chaîne à un modèle'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: d8a3c363d1a443db4a0b7633e380562af1913aca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403444"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="e27a0-102">Comment : faire correspondre une chaîne à un modèle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e27a0-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="e27a0-103">Si vous souhaitez savoir si une expression du [type de données String](../../../language-reference/data-types/string-data-type.md) est conforme à un modèle, vous pouvez utiliser l' [opérateur Like](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e27a0-103">If you want to find out if an expression of the [String Data Type](../../../language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="e27a0-104">`Like`prend deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="e27a0-104">`Like` takes two operands.</span></span> <span data-ttu-id="e27a0-105">L’opérande de gauche est une expression de chaîne et l’opérande de droite est une chaîne contenant le modèle à utiliser pour la mise en correspondance.</span><span class="sxs-lookup"><span data-stu-id="e27a0-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="e27a0-106">`Like`retourne une `Boolean` valeur indiquant si l’expression de chaîne respecte le modèle.</span><span class="sxs-lookup"><span data-stu-id="e27a0-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="e27a0-107">Vous pouvez faire correspondre chaque caractère de l’expression de chaîne à un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="e27a0-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="e27a0-108">Les positions des spécifications dans la chaîne de modèle correspondent aux positions des caractères à mettre en correspondance dans l’expression de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e27a0-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="e27a0-109">Pour faire correspondre un caractère de l’expression de chaîne à un caractère spécifique</span><span class="sxs-lookup"><span data-stu-id="e27a0-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="e27a0-110">Placez le caractère spécifique directement dans la chaîne du modèle.</span><span class="sxs-lookup"><span data-stu-id="e27a0-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="e27a0-111">Certains caractères spéciaux doivent être placés entre crochets ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="e27a0-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="e27a0-112">Pour plus d’informations, consultez [Like, opérateur](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e27a0-112">For more information, see [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="e27a0-113">L’exemple suivant teste si `myString` se compose exactement du caractère unique `H` .</span><span class="sxs-lookup"><span data-stu-id="e27a0-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="e27a0-114">Pour faire correspondre un caractère de l’expression de chaîne à un caractère générique</span><span class="sxs-lookup"><span data-stu-id="e27a0-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="e27a0-115">Placez un point d’interrogation ( `?` ) dans la chaîne du modèle.</span><span class="sxs-lookup"><span data-stu-id="e27a0-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="e27a0-116">Tout caractère valide dans cette position fait l’aboutissement d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e27a0-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="e27a0-117">L’exemple suivant teste si `myString` se compose du caractère unique `W` suivi de deux caractères exactement de toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e27a0-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="e27a0-118">Pour mettre en correspondance un caractère de l’expression de chaîne avec une liste de caractères</span><span class="sxs-lookup"><span data-stu-id="e27a0-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="e27a0-119">Placez les crochets ( `[ ]` ) dans la chaîne de modèle, et à l’intérieur des crochets, placez la liste des caractères.</span><span class="sxs-lookup"><span data-stu-id="e27a0-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="e27a0-120">Ne séparez pas les caractères par des virgules ou tout autre séparateur.</span><span class="sxs-lookup"><span data-stu-id="e27a0-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="e27a0-121">Tout caractère unique de la liste fait l’aboutissement d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e27a0-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="e27a0-122">L’exemple suivant teste si `myString` se compose d’un caractère valide suivi de l’un des caractères `A` , `C` ou `E` .</span><span class="sxs-lookup"><span data-stu-id="e27a0-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="e27a0-123">Notez que cette correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e27a0-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="e27a0-124">Pour faire correspondre un caractère de l’expression de chaîne à une plage de caractères</span><span class="sxs-lookup"><span data-stu-id="e27a0-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="e27a0-125">Placez les crochets ( `[ ]` ) dans la chaîne de modèle, et à l’intérieur des crochets, placez les caractères les plus bas et les plus hauts dans la plage, séparés par un trait d’Union ( `–` ).</span><span class="sxs-lookup"><span data-stu-id="e27a0-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="e27a0-126">Tout caractère unique dans la plage fait l’aboutissement d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e27a0-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="e27a0-127">L’exemple suivant teste si `myString` se compose des caractères `num` suivis de l’un des caractères,,,, `i` `j` `k` `l` `m` ou `n` .</span><span class="sxs-lookup"><span data-stu-id="e27a0-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="e27a0-128">Notez que cette correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e27a0-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="e27a0-129">Correspondance de chaînes vides</span><span class="sxs-lookup"><span data-stu-id="e27a0-129">Matching Empty Strings</span></span>

<span data-ttu-id="e27a0-130">`Like`traite la séquence `[]` comme une chaîne de longueur nulle ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="e27a0-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="e27a0-131">Vous pouvez utiliser `[]` pour tester si la totalité de l’expression de chaîne est vide, mais vous ne pouvez pas l’utiliser pour tester si une position particulière dans l’expression de chaîne est vide.</span><span class="sxs-lookup"><span data-stu-id="e27a0-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="e27a0-132">Si une position vide est l’une des options dont vous avez besoin pour tester, vous pouvez utiliser `Like` plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e27a0-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="e27a0-133">Pour mettre en correspondance un caractère de l’expression de chaîne avec une liste de caractères ou aucun caractère</span><span class="sxs-lookup"><span data-stu-id="e27a0-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="e27a0-134">Appelez l' `Like` opérateur deux fois sur la même expression de chaîne et connectez les deux appels à l’aide de l' [opérateur or](../../../language-reference/operators/or-operator.md) ou de l' [opérateur OrElse](../../../language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e27a0-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../language-reference/operators/or-operator.md) or the [OrElse Operator](../../../language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="e27a0-135">Dans la chaîne de modèle de la première `Like` clause, incluez la liste de caractères entre crochets ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="e27a0-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="e27a0-136">Dans la chaîne de modèle de la deuxième `Like` clause, ne placez pas de caractère à la position en question.</span><span class="sxs-lookup"><span data-stu-id="e27a0-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="e27a0-137">L’exemple suivant teste le numéro de téléphone à sept chiffres `phoneNum` pour exactement trois chiffres, suivis d’un espace, d’un trait d’Union ( `–` ), d’un point ( `.` ) ou d’aucun caractère, suivi de quatre chiffres exactement.</span><span class="sxs-lookup"><span data-stu-id="e27a0-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="e27a0-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e27a0-138">See also</span></span>

- [<span data-ttu-id="e27a0-139">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="e27a0-139">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="e27a0-140">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="e27a0-140">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="e27a0-141">Like, opérateur</span><span class="sxs-lookup"><span data-stu-id="e27a0-141">Like Operator</span></span>](../../../language-reference/operators/like-operator.md)
- [<span data-ttu-id="e27a0-142">String, type de données</span><span class="sxs-lookup"><span data-stu-id="e27a0-142">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
