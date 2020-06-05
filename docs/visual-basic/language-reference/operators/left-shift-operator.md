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
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370633"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="70bd7-102">\<\<(Visual Basic), opérateur</span><span class="sxs-lookup"><span data-stu-id="70bd7-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="70bd7-103">Effectue un décalage arithmétique vers la gauche sur un modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70bd7-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="70bd7-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="70bd7-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="70bd7-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-106">Required.</span></span> <span data-ttu-id="70bd7-107">Valeur numérique intégrale.</span><span class="sxs-lookup"><span data-stu-id="70bd7-107">Integral numeric value.</span></span> <span data-ttu-id="70bd7-108">Résultat du décalage du modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="70bd7-109">Le type de données est le même que celui de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="70bd7-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="70bd7-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-110">Required.</span></span> <span data-ttu-id="70bd7-111">Expression numérique entière.</span><span class="sxs-lookup"><span data-stu-id="70bd7-111">Integral numeric expression.</span></span> <span data-ttu-id="70bd7-112">Modèle binaire qui doit être décalé.</span><span class="sxs-lookup"><span data-stu-id="70bd7-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="70bd7-113">Le type de données doit être un type entier (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="70bd7-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="70bd7-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-114">Required.</span></span> <span data-ttu-id="70bd7-115">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="70bd7-115">Numeric expression.</span></span> <span data-ttu-id="70bd7-116">Nombre de bits pour décaler le modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="70bd7-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="70bd7-117">Le type de données doit être `Integer` ou étendu à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="70bd7-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70bd7-118">Notes</span><span class="sxs-lookup"><span data-stu-id="70bd7-118">Remarks</span></span>  
 <span data-ttu-id="70bd7-119">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="70bd7-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="70bd7-120">Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="70bd7-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="70bd7-121">Pour empêcher un décalage de plus de bits que le résultat ne peut en contenir, Visual Basic masque la valeur de `amount` avec un masque de taille qui correspond au type de données de `pattern` .</span><span class="sxs-lookup"><span data-stu-id="70bd7-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="70bd7-122">Le binaire et de ces valeurs est utilisé pour la valeur de décalage.</span><span class="sxs-lookup"><span data-stu-id="70bd7-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="70bd7-123">Les masques de taille sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="70bd7-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="70bd7-124">Type de données de`pattern`</span><span class="sxs-lookup"><span data-stu-id="70bd7-124">Data type of `pattern`</span></span>|<span data-ttu-id="70bd7-125">Masque de taille (décimal)</span><span class="sxs-lookup"><span data-stu-id="70bd7-125">Size mask (decimal)</span></span>|<span data-ttu-id="70bd7-126">Masque de taille (hexadécimal)</span><span class="sxs-lookup"><span data-stu-id="70bd7-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="70bd7-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="70bd7-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="70bd7-128">7</span><span class="sxs-lookup"><span data-stu-id="70bd7-128">7</span></span>|<span data-ttu-id="70bd7-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="70bd7-129">&H00000007</span></span>|  
|<span data-ttu-id="70bd7-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="70bd7-130">`Short`, `UShort`</span></span>|<span data-ttu-id="70bd7-131">15</span><span class="sxs-lookup"><span data-stu-id="70bd7-131">15</span></span>|<span data-ttu-id="70bd7-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="70bd7-132">&H0000000F</span></span>|  
|<span data-ttu-id="70bd7-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="70bd7-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="70bd7-134">31</span><span class="sxs-lookup"><span data-stu-id="70bd7-134">31</span></span>|<span data-ttu-id="70bd7-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="70bd7-135">&H0000001F</span></span>|  
|<span data-ttu-id="70bd7-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="70bd7-136">`Long`, `ULong`</span></span>|<span data-ttu-id="70bd7-137">63</span><span class="sxs-lookup"><span data-stu-id="70bd7-137">63</span></span>|<span data-ttu-id="70bd7-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="70bd7-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="70bd7-139">Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern` .</span><span class="sxs-lookup"><span data-stu-id="70bd7-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="70bd7-140">Si `amount` est négatif, il est considéré comme une valeur non signée et masqué avec le masque de taille approprié.</span><span class="sxs-lookup"><span data-stu-id="70bd7-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="70bd7-141">Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="70bd7-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70bd7-142">L' `<<` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="70bd7-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="70bd7-143">Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="70bd7-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="70bd7-144">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="70bd7-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70bd7-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="70bd7-145">Example</span></span>  
 <span data-ttu-id="70bd7-146">L’exemple suivant utilise l' `<<` opérateur pour effectuer des décalages arithmétiques vers la gauche sur les valeurs intégrales.</span><span class="sxs-lookup"><span data-stu-id="70bd7-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="70bd7-147">Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.</span><span class="sxs-lookup"><span data-stu-id="70bd7-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="70bd7-148">Les résultats de l’exemple précédent sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="70bd7-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="70bd7-149">`result1`est 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="70bd7-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="70bd7-150">`result2`est 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="70bd7-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="70bd7-151">`result3`est-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="70bd7-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="70bd7-152">`result4`est 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="70bd7-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="70bd7-153">`result5`est 0 (décalé de 15 places vers la gauche).</span><span class="sxs-lookup"><span data-stu-id="70bd7-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="70bd7-154">Le nombre de décalages pour `result4` est calculé comme 17 et 15, ce qui équivaut à 1.</span><span class="sxs-lookup"><span data-stu-id="70bd7-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bd7-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70bd7-155">See also</span></span>

- [<span data-ttu-id="70bd7-156">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="70bd7-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="70bd7-157">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="70bd7-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="70bd7-158"><<=, opérateur</span><span class="sxs-lookup"><span data-stu-id="70bd7-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="70bd7-159">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70bd7-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="70bd7-160">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="70bd7-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="70bd7-161">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70bd7-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
