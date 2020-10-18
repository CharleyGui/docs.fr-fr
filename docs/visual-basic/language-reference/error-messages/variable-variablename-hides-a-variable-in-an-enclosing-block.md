---
title: La variable '<variablename>'masque une variable dans un bloc englobant
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161346"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="c3a39-102">BC30616 : la variable' \<variablename> 'masque une variable dans un bloc englobant</span><span class="sxs-lookup"><span data-stu-id="c3a39-102">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="c3a39-103">Une variable comprise dans un bloc porte le même nom qu’une autre variable locale.</span><span class="sxs-lookup"><span data-stu-id="c3a39-103">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="c3a39-104">**ID d’erreur :** BC30616</span><span class="sxs-lookup"><span data-stu-id="c3a39-104">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c3a39-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c3a39-105">To correct this error</span></span>

- <span data-ttu-id="c3a39-106">Renommez la variable dans le bloc délimité afin qu’elle ne soit pas la même que les autres variables locales.</span><span class="sxs-lookup"><span data-stu-id="c3a39-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="c3a39-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c3a39-107">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="c3a39-108">Une cause courante de cette erreur est l’utilisation de `Catch e As Exception` dans un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="c3a39-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="c3a39-109">Si c’est le cas, nommez la `Catch` variable de bloc `ex` plutôt que `e` .</span><span class="sxs-lookup"><span data-stu-id="c3a39-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="c3a39-110">Une autre source courante de cette erreur est une tentative d’accès à une variable locale déclarée dans un `Try` bloc dans un `Catch` bloc séparé.</span><span class="sxs-lookup"><span data-stu-id="c3a39-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="c3a39-111">Pour corriger cela, déclarez la variable en dehors de la `Try...Catch...Finally` structure.</span><span class="sxs-lookup"><span data-stu-id="c3a39-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3a39-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3a39-112">See also</span></span>

- [<span data-ttu-id="c3a39-113">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="c3a39-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="c3a39-114">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="c3a39-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
