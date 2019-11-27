---
title: 'Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346816"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="bee33-102">Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bee33-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="bee33-103">Si vous accédez fréquemment à un objet qui requiert un chemin d’accès de qualification de plusieurs méthodes et propriétés, vous pouvez accélérer votre code en ne répétant pas le chemin d’accès de qualification.</span><span class="sxs-lookup"><span data-stu-id="bee33-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="bee33-104">Vous pouvez éviter de répéter le chemin d’accès de qualification de deux manières.</span><span class="sxs-lookup"><span data-stu-id="bee33-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="bee33-105">Vous pouvez assigner l’objet à une variable, ou vous pouvez l’utiliser dans un bloc `With`...`End With`.</span><span class="sxs-lookup"><span data-stu-id="bee33-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="bee33-106">Pour accélérer l’accès à un objet très qualifié en l’assignant à une variable</span><span class="sxs-lookup"><span data-stu-id="bee33-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="bee33-107">Déclarez une variable du type de l’objet auquel vous accédez fréquemment.</span><span class="sxs-lookup"><span data-stu-id="bee33-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="bee33-108">Spécifiez le chemin d’accès de qualification dans la partie initialisation de la déclaration.</span><span class="sxs-lookup"><span data-stu-id="bee33-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="bee33-109">Utilisez la variable pour accéder aux membres de l’objet.</span><span class="sxs-lookup"><span data-stu-id="bee33-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="bee33-110">Pour accélérer l’accès à un objet très qualifié à l’aide d’un avec... Terminer par un bloc</span><span class="sxs-lookup"><span data-stu-id="bee33-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="bee33-111">Placez le chemin d’accès de qualification dans une instruction `With`.</span><span class="sxs-lookup"><span data-stu-id="bee33-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="bee33-112">Accédez aux membres de l’objet à l’intérieur du bloc `With`, avant l’instruction `End With`.</span><span class="sxs-lookup"><span data-stu-id="bee33-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="bee33-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bee33-113">See also</span></span>

- [<span data-ttu-id="bee33-114">Variables objets</span><span class="sxs-lookup"><span data-stu-id="bee33-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="bee33-115">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="bee33-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
