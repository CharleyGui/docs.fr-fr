---
title: Opérateurs de concaténation
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388788"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="20536-102">Opérateurs de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20536-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="20536-103">Les opérateurs de concaténation joignent plusieurs chaînes en une seule.</span><span class="sxs-lookup"><span data-stu-id="20536-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="20536-104">Il existe deux opérateurs de concaténation, `+` et `&`.</span><span class="sxs-lookup"><span data-stu-id="20536-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="20536-105">Les deux effectuent l'opération de concaténation de base, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="20536-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="20536-106">Ces opérateurs peuvent également concaténer les variables `String`, comme illustré ici.</span><span class="sxs-lookup"><span data-stu-id="20536-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="20536-107">Différences entre ces deux opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="20536-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="20536-108">L' [opérateur +](../../../language-reference/operators/addition-operator.md) a l’objectif principal d’ajouter deux nombres.</span><span class="sxs-lookup"><span data-stu-id="20536-108">The [+ Operator](../../../language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="20536-109">Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="20536-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="20536-110">L'opérateur `+` comporte un ensemble complexe de règles qui déterminent s'il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exception <xref:System.InvalidCastException> d'exécution.</span><span class="sxs-lookup"><span data-stu-id="20536-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="20536-111">L' [opérateur&](../../../language-reference/operators/concatenation-operator.md) est défini uniquement pour les `String` opérandes, et il élargit toujours ses opérandes à `String` , quel que soit le paramètre de `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="20536-111">The [& Operator](../../../language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="20536-112">L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.</span><span class="sxs-lookup"><span data-stu-id="20536-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="20536-113">Performance : String et StringBuilder</span><span class="sxs-lookup"><span data-stu-id="20536-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="20536-114">Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, suppressions et remplacements, vos performances peuvent s'améliorer avec la classe <xref:System.Text.StringBuilder> de l'espace de noms <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="20536-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="20536-115">Elle prend une instruction supplémentaire pour créer et initialiser un objet <xref:System.Text.StringBuilder>, et une autre instruction pour convertir sa valeur finale en une `String`, mais vous pouvez rattraper le retard induit car <xref:System.Text.StringBuilder> peut s'exécuter plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="20536-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="20536-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20536-116">See also</span></span>

- [<span data-ttu-id="20536-117">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="20536-117">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="20536-118">Types de méthodes de manipulation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20536-118">Types of String Manipulation Methods in Visual Basic</span></span>](../strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="20536-119">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20536-119">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="20536-120">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20536-120">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="20536-121">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20536-121">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
