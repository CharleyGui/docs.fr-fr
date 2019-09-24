---
title: 'Procédure : Créer une procédure (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216723"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="61a08-102">Procédure : Créer une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61a08-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="61a08-103">Vous devez placer une procédure entre une instruction de début`Sub` de `Function`déclaration (ou) et une instruction`End Sub` de `End Function`déclaration de fin (ou).</span><span class="sxs-lookup"><span data-stu-id="61a08-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="61a08-104">Tout le code de la procédure se trouve entre ces instructions.</span><span class="sxs-lookup"><span data-stu-id="61a08-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="61a08-105">Une procédure ne peut pas contenir une autre procédure, donc ses instructions de début et de fin doivent être en dehors de toute autre procédure.</span><span class="sxs-lookup"><span data-stu-id="61a08-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="61a08-106">Si vous avez du code qui effectue la même tâche dans différents emplacements, vous pouvez écrire la tâche une seule fois en tant que procédure, puis l’appeler à partir de différents emplacements dans votre code.</span><span class="sxs-lookup"><span data-stu-id="61a08-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="61a08-107">Pour créer une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="61a08-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="61a08-108">En dehors de toute autre procédure, `Sub` utilisez une instruction, suivie `End Sub` d’une instruction.</span><span class="sxs-lookup"><span data-stu-id="61a08-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="61a08-109">Dans l' `Sub` instruction, `Sub` suivez le mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="61a08-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="61a08-110">Placez les instructions de code de la procédure `Sub` entre `End Sub` les instructions et.</span><span class="sxs-lookup"><span data-stu-id="61a08-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="61a08-111">Pour créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="61a08-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="61a08-112">En dehors de toute autre procédure, `Function` utilisez une instruction, suivie `End Function` d’une instruction.</span><span class="sxs-lookup"><span data-stu-id="61a08-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="61a08-113">Dans l' `Function` instruction, `Function` suivez le mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses, et `As` enfin une clause qui spécifie le type de données de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="61a08-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="61a08-114">Placez les instructions de code de la procédure `Function` entre `End Function` les instructions et.</span><span class="sxs-lookup"><span data-stu-id="61a08-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="61a08-115">Utilisez une `Return` instruction pour retourner la valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="61a08-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="61a08-116">Pour connecter votre nouvelle procédure avec les anciens blocs de code répétitifs</span><span class="sxs-lookup"><span data-stu-id="61a08-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="61a08-117">Veillez à définir la nouvelle procédure à un endroit où l’ancien code y a accès.</span><span class="sxs-lookup"><span data-stu-id="61a08-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="61a08-118">Dans votre ancien bloc de code répétitif, remplacez les instructions qui exécutent la tâche répétitive par une instruction unique qui appelle `Sub` la `Function` procédure ou.</span><span class="sxs-lookup"><span data-stu-id="61a08-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="61a08-119">Si votre procédure est un `Function` qui retourne une valeur, assurez-vous que votre instruction appelante effectue une action avec la valeur retournée, telle que le stockage dans une variable, sinon la valeur sera perdue.</span><span class="sxs-lookup"><span data-stu-id="61a08-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="61a08-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="61a08-120">Example</span></span>

 <span data-ttu-id="61a08-121">La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés :</span><span class="sxs-lookup"><span data-stu-id="61a08-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="61a08-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a08-122">See also</span></span>

- [<span data-ttu-id="61a08-123">Procédures</span><span class="sxs-lookup"><span data-stu-id="61a08-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="61a08-124">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="61a08-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="61a08-125">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="61a08-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="61a08-126">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="61a08-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="61a08-127">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="61a08-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="61a08-128">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="61a08-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="61a08-129">Procédures récursives</span><span class="sxs-lookup"><span data-stu-id="61a08-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="61a08-130">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="61a08-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="61a08-131">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="61a08-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="61a08-132">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61a08-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
