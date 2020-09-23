---
title: 'Comment : définir un opérateur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 5acbd0439ddbb956b80d56e23d11cd5e152f37ff
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087399"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="cc997-102">Comment : définir un opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc997-102">How to: Define an Operator (Visual Basic)</span></span>

<span data-ttu-id="cc997-103">Si vous avez défini une classe ou une structure, vous pouvez définir le comportement d’un opérateur standard (tel que `*` , `<>` ou `And` ) quand l’un des opérandes ou les deux sont du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="cc997-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="cc997-104">Définissez l’opérateur standard comme une procédure d’opérateur dans la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="cc997-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="cc997-105">Toutes les procédures d’opérateur doivent être `Public` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="cc997-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="cc997-106">La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="cc997-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc997-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc997-107">Example</span></span>  

 <span data-ttu-id="cc997-108">L’exemple suivant définit l' `+` opérateur pour une structure appelée `height` .</span><span class="sxs-lookup"><span data-stu-id="cc997-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="cc997-109">La structure utilise des hauteurs mesurées en mètres et en pouces.</span><span class="sxs-lookup"><span data-stu-id="cc997-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="cc997-110">Un *pouce* est de 2,54 centimètres, et un *pied* est de 12 pouces.</span><span class="sxs-lookup"><span data-stu-id="cc997-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="cc997-111">Pour garantir des valeurs normalisées (pouces < 12,0), le constructeur effectue une opération arithmétique *modulo* 12.</span><span class="sxs-lookup"><span data-stu-id="cc997-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="cc997-112">L' `+` opérateur utilise le constructeur pour générer des valeurs normalisées.</span><span class="sxs-lookup"><span data-stu-id="cc997-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="cc997-113">Vous pouvez tester la structure `height` à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="cc997-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="cc997-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc997-114">See also</span></span>

- [<span data-ttu-id="cc997-115">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="cc997-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cc997-116">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="cc997-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="cc997-117">Comment : appeler une procédure d'opérateur</span><span class="sxs-lookup"><span data-stu-id="cc997-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="cc997-118">Comment : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="cc997-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="cc997-119">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="cc997-119">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="cc997-120">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="cc997-120">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="cc997-121">Procédure : Déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="cc997-121">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="cc997-122">Mod, opérateur</span><span class="sxs-lookup"><span data-stu-id="cc997-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
