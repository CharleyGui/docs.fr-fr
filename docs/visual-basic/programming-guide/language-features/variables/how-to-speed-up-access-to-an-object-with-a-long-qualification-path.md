---
title: "Comment : accélérer l'accès à un objet comportant un chemin d'accès de qualification long"
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
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="1e02f-102">Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e02f-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="1e02f-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span><span class="sxs-lookup"><span data-stu-id="1e02f-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="1e02f-104">There are two ways you can avoid repeating the qualification path.</span><span class="sxs-lookup"><span data-stu-id="1e02f-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="1e02f-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span><span class="sxs-lookup"><span data-stu-id="1e02f-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="1e02f-106">To speed up access to a heavily qualified object by assigning it to a variable</span><span class="sxs-lookup"><span data-stu-id="1e02f-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="1e02f-107">Declare a variable of the type of the object that you are accessing frequently.</span><span class="sxs-lookup"><span data-stu-id="1e02f-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="1e02f-108">Specify the qualification path in the initialization part of the declaration.</span><span class="sxs-lookup"><span data-stu-id="1e02f-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="1e02f-109">Use the variable to access the object's members.</span><span class="sxs-lookup"><span data-stu-id="1e02f-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="1e02f-110">To speed up access to a heavily qualified object by using a With...End With block</span><span class="sxs-lookup"><span data-stu-id="1e02f-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="1e02f-111">Put the qualification path in a `With` statement.</span><span class="sxs-lookup"><span data-stu-id="1e02f-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="1e02f-112">Access the object's members inside the `With` block, before the `End With` statement.</span><span class="sxs-lookup"><span data-stu-id="1e02f-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="1e02f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e02f-113">See also</span></span>

- [<span data-ttu-id="1e02f-114">Variables objets</span><span class="sxs-lookup"><span data-stu-id="1e02f-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="1e02f-115">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="1e02f-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
