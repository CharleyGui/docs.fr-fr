---
title: 'Comment : définir un opérateur de conversion'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085670"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="ed69e-102">Comment : définir un opérateur de conversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed69e-102">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="ed69e-103">Si vous avez défini une classe ou une structure, vous pouvez définir un opérateur de conversion de type entre le type de votre classe ou structure et un autre type de données (tel que `Integer` , `Double` ou `String` ).</span><span class="sxs-lookup"><span data-stu-id="ed69e-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="ed69e-104">Définissez la conversion de type comme une procédure de [fonction CType](../../../language-reference/functions/ctype-function.md) dans la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="ed69e-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="ed69e-105">Toutes les procédures de conversion doivent avoir la `Public Shared` valeur et chacune d’elles doit spécifier l' [élargissement](../../../language-reference/modifiers/widening.md) ou la [réduction](../../../language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="ed69e-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="ed69e-106">La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="ed69e-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed69e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed69e-107">Example</span></span>  

 <span data-ttu-id="ed69e-108">L’exemple suivant définit des opérateurs de conversion entre une structure appelée `digit` et un `Byte` .</span><span class="sxs-lookup"><span data-stu-id="ed69e-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="ed69e-109">Vous pouvez tester la structure `digit` à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="ed69e-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="ed69e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed69e-110">See also</span></span>

- [<span data-ttu-id="ed69e-111">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="ed69e-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ed69e-112">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="ed69e-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="ed69e-113">Comment : appeler une procédure d'opérateur</span><span class="sxs-lookup"><span data-stu-id="ed69e-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="ed69e-114">Comment : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="ed69e-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="ed69e-115">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="ed69e-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ed69e-116">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="ed69e-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="ed69e-117">Procédure : Déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="ed69e-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ed69e-118">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="ed69e-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="ed69e-119">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="ed69e-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
