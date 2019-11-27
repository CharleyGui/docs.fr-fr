---
title: <<, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350983"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="49c4f-102">\<\<, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49c4f-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="49c4f-103">Effectue un décalage arithmétique vers la gauche sur un modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="49c4f-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49c4f-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="49c4f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="49c4f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="49c4f-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="49c4f-106">Required.</span></span> <span data-ttu-id="49c4f-107">Valeur numérique intégrale.</span><span class="sxs-lookup"><span data-stu-id="49c4f-107">Integral numeric value.</span></span> <span data-ttu-id="49c4f-108">Résultat de l’évolution du modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="49c4f-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="49c4f-109">Le type de données est le même que celui de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="49c4f-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="49c4f-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="49c4f-110">Required.</span></span> <span data-ttu-id="49c4f-111">Expression numérique intégrale.</span><span class="sxs-lookup"><span data-stu-id="49c4f-111">Integral numeric expression.</span></span> <span data-ttu-id="49c4f-112">Modèle binaire à décaler.</span><span class="sxs-lookup"><span data-stu-id="49c4f-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="49c4f-113">Le type de données doit être un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="49c4f-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="49c4f-114">Requis.</span><span class="sxs-lookup"><span data-stu-id="49c4f-114">Required.</span></span> <span data-ttu-id="49c4f-115">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="49c4f-115">Numeric expression.</span></span> <span data-ttu-id="49c4f-116">Nombre de bits de décalage du modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="49c4f-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="49c4f-117">Le type de données doit être `Integer` ou étendu à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="49c4f-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49c4f-118">Notes</span><span class="sxs-lookup"><span data-stu-id="49c4f-118">Remarks</span></span>  
 <span data-ttu-id="49c4f-119">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="49c4f-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="49c4f-120">Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="49c4f-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="49c4f-121">Pour empêcher un décalage de plus de bits que le résultat ne peut en contenir, Visual Basic masque la valeur de `amount` avec un masque de taille qui correspond au type de données de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="49c4f-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="49c4f-122">Le binaire et de ces valeurs est utilisé pour la valeur de décalage.</span><span class="sxs-lookup"><span data-stu-id="49c4f-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="49c4f-123">Les masques de taille sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="49c4f-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="49c4f-124">Type de données de `pattern`</span><span class="sxs-lookup"><span data-stu-id="49c4f-124">Data type of `pattern`</span></span>|<span data-ttu-id="49c4f-125">Masque de taille (décimal)</span><span class="sxs-lookup"><span data-stu-id="49c4f-125">Size mask (decimal)</span></span>|<span data-ttu-id="49c4f-126">Masque de taille (hexadécimal)</span><span class="sxs-lookup"><span data-stu-id="49c4f-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="49c4f-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="49c4f-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="49c4f-128">7</span><span class="sxs-lookup"><span data-stu-id="49c4f-128">7</span></span>|<span data-ttu-id="49c4f-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="49c4f-129">&H00000007</span></span>|  
|<span data-ttu-id="49c4f-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="49c4f-130">`Short`, `UShort`</span></span>|<span data-ttu-id="49c4f-131">15</span><span class="sxs-lookup"><span data-stu-id="49c4f-131">15</span></span>|<span data-ttu-id="49c4f-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="49c4f-132">&H0000000F</span></span>|  
|<span data-ttu-id="49c4f-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="49c4f-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="49c4f-134">31</span><span class="sxs-lookup"><span data-stu-id="49c4f-134">31</span></span>|<span data-ttu-id="49c4f-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="49c4f-135">&H0000001F</span></span>|  
|<span data-ttu-id="49c4f-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="49c4f-136">`Long`, `ULong`</span></span>|<span data-ttu-id="49c4f-137">63</span><span class="sxs-lookup"><span data-stu-id="49c4f-137">63</span></span>|<span data-ttu-id="49c4f-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="49c4f-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="49c4f-139">Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="49c4f-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="49c4f-140">Si `amount` est négatif, il est considéré comme une valeur non signée et est masqué avec le masque de taille approprié.</span><span class="sxs-lookup"><span data-stu-id="49c4f-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="49c4f-141">Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="49c4f-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49c4f-142">L’opérateur `<<` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="49c4f-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="49c4f-143">Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="49c4f-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="49c4f-144">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="49c4f-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c4f-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="49c4f-145">Example</span></span>  
 <span data-ttu-id="49c4f-146">L’exemple suivant utilise l’opérateur `<<` pour effectuer des décalages arithmétiques vers la gauche sur les valeurs intégrales.</span><span class="sxs-lookup"><span data-stu-id="49c4f-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="49c4f-147">Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.</span><span class="sxs-lookup"><span data-stu-id="49c4f-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="49c4f-148">Les résultats de l’exemple précédent sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="49c4f-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="49c4f-149">`result1` est 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="49c4f-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="49c4f-150">`result2` est 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="49c4f-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="49c4f-151">`result3` est-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="49c4f-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="49c4f-152">`result4` est 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="49c4f-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="49c4f-153">`result5` a la valeur 0 (décalée de 15 places vers la gauche).</span><span class="sxs-lookup"><span data-stu-id="49c4f-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="49c4f-154">Le nombre de décalages pour `result4` est calculé comme 17 et 15, ce qui équivaut à 1.</span><span class="sxs-lookup"><span data-stu-id="49c4f-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c4f-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49c4f-155">See also</span></span>

- [<span data-ttu-id="49c4f-156">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="49c4f-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="49c4f-157">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="49c4f-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="49c4f-158"><<=, opérateur</span><span class="sxs-lookup"><span data-stu-id="49c4f-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="49c4f-159">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49c4f-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="49c4f-160">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="49c4f-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="49c4f-161">Opérateurs arithmétiques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49c4f-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
