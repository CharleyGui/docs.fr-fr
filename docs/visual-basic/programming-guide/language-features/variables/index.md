---
title: Variables
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410385"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="b930b-102">Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b930b-102">Variables in Visual Basic</span></span>
<span data-ttu-id="b930b-103">Vous devez souvent stocker des valeurs lorsque vous effectuez des calculs avec Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b930b-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="b930b-104">Par exemple, vous pouvez être amené à calculer plusieurs valeurs, à les comparer et à effectuer différentes opérations sur ces valeurs, en fonction du résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="b930b-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="b930b-105">Vous devez conserver les valeurs si vous souhaitez les comparer.</span><span class="sxs-lookup"><span data-stu-id="b930b-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b930b-106">Usage</span><span class="sxs-lookup"><span data-stu-id="b930b-106">Usage</span></span>  
 <span data-ttu-id="b930b-107">Visual Basic, tout comme la plupart des langages de programmation, utilise des variables pour stocker les valeurs.</span><span class="sxs-lookup"><span data-stu-id="b930b-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="b930b-108">Une *variable* a un nom (le mot que vous utilisez pour faire référence à la valeur que la variable contient).</span><span class="sxs-lookup"><span data-stu-id="b930b-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="b930b-109">Une variable a également un type de données (lequel détermine le genre des données que la variable peut stocker).</span><span class="sxs-lookup"><span data-stu-id="b930b-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="b930b-110">Une variable peut représenter un tableau si elle doit stocker un ensemble indexé d’éléments de données étroitement liés.</span><span class="sxs-lookup"><span data-stu-id="b930b-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="b930b-111">L’inférence de type de variable locale vous permet de déclarer des variables sans déclarer explicitement un type de données.</span><span class="sxs-lookup"><span data-stu-id="b930b-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="b930b-112">À la place, le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="b930b-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="b930b-113">Pour plus d’informations, consultez [Inférence de type de variable locale](local-type-inference.md) et [Option Infer, instruction](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b930b-113">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="b930b-114">Assignation de valeurs</span><span class="sxs-lookup"><span data-stu-id="b930b-114">Assigning Values</span></span>  
 <span data-ttu-id="b930b-115">Vous utilisez des instructions d’assignation pour effectuer des calculs et assigner le résultat à une variable, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b930b-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="b930b-116">Dans cet exemple, le signe égal (`=`) représente un opérateur d’assignation, et non un opérateur d’égalité.</span><span class="sxs-lookup"><span data-stu-id="b930b-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="b930b-117">La valeur est assignée à la variable `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="b930b-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="b930b-118">Pour plus d’informations, consultez [Guide pratique pour placer des données dans et en dehors d’une variable](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="b930b-118">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="b930b-119">Variables et propriétés</span><span class="sxs-lookup"><span data-stu-id="b930b-119">Variables and Properties</span></span>  
 <span data-ttu-id="b930b-120">À l’instar d’une variable, une *propriété* représente une valeur à laquelle vous pouvez accéder.</span><span class="sxs-lookup"><span data-stu-id="b930b-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="b930b-121">Toutefois, elle est plus complexe qu’une variable.</span><span class="sxs-lookup"><span data-stu-id="b930b-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="b930b-122">Une propriété utilise des blocs de code qui contrôlent la définition et la récupération de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="b930b-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="b930b-123">Pour plus d’informations, consultez [Différences entre les propriétés et les variables en Visual Basic](../procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b930b-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b930b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b930b-124">See also</span></span>

- [<span data-ttu-id="b930b-125">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="b930b-125">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="b930b-126">Variables objets</span><span class="sxs-lookup"><span data-stu-id="b930b-126">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="b930b-127">Dépannage des variables</span><span class="sxs-lookup"><span data-stu-id="b930b-127">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="b930b-128">Comment : placer des données dans et en dehors d'une variable</span><span class="sxs-lookup"><span data-stu-id="b930b-128">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="b930b-129">Différences entre les propriétés et les variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b930b-129">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="b930b-130">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="b930b-130">Local Type Inference</span></span>](local-type-inference.md)
