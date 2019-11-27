---
title: 'Comment : créer une procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344908"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="42d23-102">Comment : créer une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42d23-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="42d23-103">Vous devez placer une procédure entre une instruction de déclaration de départ (`Sub` ou `Function`) et une instruction de déclaration de fin (`End Sub` ou `End Function`).</span><span class="sxs-lookup"><span data-stu-id="42d23-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="42d23-104">Tout le code de la procédure se trouve entre ces instructions.</span><span class="sxs-lookup"><span data-stu-id="42d23-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="42d23-105">Une procédure ne peut pas contenir une autre procédure, donc ses instructions de début et de fin doivent être en dehors de toute autre procédure.</span><span class="sxs-lookup"><span data-stu-id="42d23-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="42d23-106">Si vous avez du code qui effectue la même tâche dans différents emplacements, vous pouvez écrire la tâche une seule fois en tant que procédure, puis l’appeler à partir de différents emplacements dans votre code.</span><span class="sxs-lookup"><span data-stu-id="42d23-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="42d23-107">Pour créer une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="42d23-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="42d23-108">En dehors de toute autre procédure, utilisez une instruction `Sub`, suivie d’une instruction `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="42d23-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="42d23-109">Dans l’instruction `Sub`, suivez le mot clé `Sub` avec le nom de la procédure, puis la liste de paramètres entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="42d23-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="42d23-110">Placez les instructions de code de la procédure entre les instructions `Sub` et `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="42d23-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="42d23-111">Pour créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="42d23-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="42d23-112">En dehors de toute autre procédure, utilisez une instruction `Function`, suivie d’une instruction `End Function`.</span><span class="sxs-lookup"><span data-stu-id="42d23-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="42d23-113">Dans l’instruction `Function`, suivez le mot clé `Function` avec le nom de la procédure, la liste de paramètres entre parenthèses, puis une clause `As` en spécifiant le type de données de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="42d23-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="42d23-114">Placez les instructions de code de la procédure entre les instructions `Function` et `End Function`.</span><span class="sxs-lookup"><span data-stu-id="42d23-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="42d23-115">Utilisez une instruction `Return` pour retourner la valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="42d23-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="42d23-116">Pour connecter votre nouvelle procédure avec les anciens blocs de code répétitifs</span><span class="sxs-lookup"><span data-stu-id="42d23-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="42d23-117">Veillez à définir la nouvelle procédure à un endroit où l’ancien code y a accès.</span><span class="sxs-lookup"><span data-stu-id="42d23-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="42d23-118">Dans votre ancien bloc de code répétitif, remplacez les instructions qui exécutent la tâche répétitive par une instruction unique qui appelle la procédure `Sub` ou `Function`.</span><span class="sxs-lookup"><span data-stu-id="42d23-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="42d23-119">Si votre procédure est un `Function` qui retourne une valeur, assurez-vous que votre instruction appelante effectue une action avec la valeur retournée, telle que son stockage dans une variable, sinon la valeur sera perdue.</span><span class="sxs-lookup"><span data-stu-id="42d23-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="42d23-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="42d23-120">Example</span></span>

 <span data-ttu-id="42d23-121">La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés :</span><span class="sxs-lookup"><span data-stu-id="42d23-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="42d23-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42d23-122">See also</span></span>

- [<span data-ttu-id="42d23-123">Procédures</span><span class="sxs-lookup"><span data-stu-id="42d23-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="42d23-124">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="42d23-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="42d23-125">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="42d23-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="42d23-126">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="42d23-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="42d23-127">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="42d23-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="42d23-128">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="42d23-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="42d23-129">Procédures récursives</span><span class="sxs-lookup"><span data-stu-id="42d23-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="42d23-130">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="42d23-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="42d23-131">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="42d23-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="42d23-132">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42d23-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
