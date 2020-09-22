---
title: '>> Opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 00f43bc9bae6d550ed175906777ac273fc8e9a23
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873335"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0ed9f-102">Opérateur de >> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ed9f-102">>> Operator (Visual Basic)</span></span>

<span data-ttu-id="0ed9f-103">Effectue un décalage arithmétique vers la droite sur un modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ed9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ed9f-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="0ed9f-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="0ed9f-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="0ed9f-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-106">Required.</span></span> <span data-ttu-id="0ed9f-107">Valeur numérique intégrale.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-107">Integral numeric value.</span></span> <span data-ttu-id="0ed9f-108">Résultat du décalage du modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="0ed9f-109">Le type de données est le même que celui de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="0ed9f-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-110">Required.</span></span> <span data-ttu-id="0ed9f-111">Expression numérique entière.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-111">Integral numeric expression.</span></span> <span data-ttu-id="0ed9f-112">Modèle binaire qui doit être décalé.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="0ed9f-113">Le type de données doit être un type entier (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="0ed9f-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-114">Required.</span></span> <span data-ttu-id="0ed9f-115">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-115">Numeric expression.</span></span> <span data-ttu-id="0ed9f-116">Nombre de bits pour décaler le modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="0ed9f-117">Le type de données doit être `Integer` ou étendu à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ed9f-118">Notes</span><span class="sxs-lookup"><span data-stu-id="0ed9f-118">Remarks</span></span>  

 <span data-ttu-id="0ed9f-119">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="0ed9f-120">Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position du bit le plus à droite sont ignorés, et le bit le plus à gauche (signe) est propagé dans les positions de bits libérées à gauche.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="0ed9f-121">Cela signifie que si `pattern` a une valeur négative, les positions libérées sont définies sur un ; sinon, elles ont la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="0ed9f-122">Notez que les types de données `Byte` ,, `UShort` `UInteger` et `ULong` ne sont pas signés, donc il n’y a aucun bit de signe à propager.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="0ed9f-123">Si `pattern` est de type non signé, les positions libérées sont toujours définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="0ed9f-124">Pour empêcher le décalage par plus de bits que le résultat ne peut en contenir, Visual Basic masque la valeur de `amount` avec un masque de taille correspondant au type de données de `pattern` .</span><span class="sxs-lookup"><span data-stu-id="0ed9f-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="0ed9f-125">Le binaire et de ces valeurs est utilisé pour la valeur de décalage.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="0ed9f-126">Les masques de taille sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0ed9f-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="0ed9f-127">Type de données de `pattern`</span><span class="sxs-lookup"><span data-stu-id="0ed9f-127">Data type of `pattern`</span></span>|<span data-ttu-id="0ed9f-128">Masque de taille (décimal)</span><span class="sxs-lookup"><span data-stu-id="0ed9f-128">Size mask (decimal)</span></span>|<span data-ttu-id="0ed9f-129">Masque de taille (hexadécimal)</span><span class="sxs-lookup"><span data-stu-id="0ed9f-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="0ed9f-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="0ed9f-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="0ed9f-131">7</span><span class="sxs-lookup"><span data-stu-id="0ed9f-131">7</span></span>|<span data-ttu-id="0ed9f-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="0ed9f-132">&H00000007</span></span>|  
|<span data-ttu-id="0ed9f-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="0ed9f-133">`Short`, `UShort`</span></span>|<span data-ttu-id="0ed9f-134">15</span><span class="sxs-lookup"><span data-stu-id="0ed9f-134">15</span></span>|<span data-ttu-id="0ed9f-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="0ed9f-135">&H0000000F</span></span>|  
|<span data-ttu-id="0ed9f-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="0ed9f-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="0ed9f-137">31</span><span class="sxs-lookup"><span data-stu-id="0ed9f-137">31</span></span>|<span data-ttu-id="0ed9f-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="0ed9f-138">&H0000001F</span></span>|  
|<span data-ttu-id="0ed9f-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="0ed9f-139">`Long`, `ULong`</span></span>|<span data-ttu-id="0ed9f-140">63</span><span class="sxs-lookup"><span data-stu-id="0ed9f-140">63</span></span>|<span data-ttu-id="0ed9f-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="0ed9f-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="0ed9f-142">Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern` .</span><span class="sxs-lookup"><span data-stu-id="0ed9f-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="0ed9f-143">Si `amount` est négatif, il est considéré comme une valeur non signée et masqué avec le masque de taille approprié.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="0ed9f-144">Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0ed9f-145">Surcharge</span><span class="sxs-lookup"><span data-stu-id="0ed9f-145">Overloading</span></span>  

 <span data-ttu-id="0ed9f-146">L' `>>` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0ed9f-147">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0ed9f-148">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed9f-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="0ed9f-149">Example</span></span>  

 <span data-ttu-id="0ed9f-150">L’exemple suivant utilise l' `>>` opérateur pour effectuer des décalages arithmétiques vers la droite sur les valeurs intégrales.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="0ed9f-151">Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="0ed9f-152">Les résultats de l’exemple précédent sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0ed9f-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="0ed9f-153">`result1` est 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="0ed9f-154">`result2` est 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="0ed9f-155">`result3` est 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="0ed9f-156">`result4` est 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="0ed9f-157">`result5` est 0 (décalé de 15 places vers la droite).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="0ed9f-158">Le nombre de décalages pour `result4` est calculé comme 18 et 15, ce qui équivaut à 2.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="0ed9f-159">L’exemple suivant montre des décalages arithmétiques sur une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="0ed9f-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="0ed9f-160">Les résultats de l’exemple précédent sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0ed9f-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="0ed9f-161">`negresult1` est-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="0ed9f-162">`negresult2` est-1 (le bit de signe est propagé).</span><span class="sxs-lookup"><span data-stu-id="0ed9f-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed9f-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ed9f-163">See also</span></span>

- [<span data-ttu-id="0ed9f-164">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="0ed9f-164">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="0ed9f-165">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="0ed9f-165">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="0ed9f-166">>>=, opérateur</span><span class="sxs-lookup"><span data-stu-id="0ed9f-166">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="0ed9f-167">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ed9f-167">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0ed9f-168">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="0ed9f-168">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0ed9f-169">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ed9f-169">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
