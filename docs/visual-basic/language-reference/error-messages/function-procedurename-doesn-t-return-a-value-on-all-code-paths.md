---
title: La fonction '<procedurename>' ne retourne pas une valeur pour tous les chemins de code
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 19b305e337767dfb34718aed7b665f142851bd36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163361"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="c013d-102">BC42105 : la fonction' \<procedurename> 'ne retourne pas de valeur pour tous les chemins de code</span><span class="sxs-lookup"><span data-stu-id="c013d-102">BC42105: Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="c013d-103">La fonction' \<procedurename> 'ne retourne pas de valeur sur tous les chemins de code.</span><span class="sxs-lookup"><span data-stu-id="c013d-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="c013d-104">Une instruction’return’est-elle manquante ?</span><span class="sxs-lookup"><span data-stu-id="c013d-104">Are you missing a 'Return' statement?</span></span>

 <span data-ttu-id="c013d-105">Une `Function` procédure a au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="c013d-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="c013d-106">Vous pouvez retourner une valeur à partir d’une `Function` procédure de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="c013d-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>

- <span data-ttu-id="c013d-107">Incluez la valeur dans une [instruction return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c013d-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

- <span data-ttu-id="c013d-108">Assignez la valeur au nom de la `Function` procédure, puis exécutez une `Exit Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="c013d-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>

- <span data-ttu-id="c013d-109">Assignez la valeur au nom de la `Function` procédure, puis exécutez l' `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="c013d-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>

 <span data-ttu-id="c013d-110">Si le contrôle est transmis à `Exit Function` ou `End Function` et que vous n’avez affecté aucune valeur au nom de la procédure, la procédure retourne la valeur par défaut du type de données de retour.</span><span class="sxs-lookup"><span data-stu-id="c013d-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="c013d-111">Pour plus d’informations, consultez « Behavior » dans l' [instruction de fonction](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c013d-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

 <span data-ttu-id="c013d-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="c013d-112">By default, this message is a warning.</span></span> <span data-ttu-id="c013d-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c013d-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c013d-114">**ID d’erreur :** BC42105</span><span class="sxs-lookup"><span data-stu-id="c013d-114">**Error ID:** BC42105</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c013d-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c013d-115">To correct this error</span></span>

- <span data-ttu-id="c013d-116">Vérifiez votre logique de workflow de contrôle et assurez-vous que vous attribuez une valeur avant chaque instruction qui provoque un retour.</span><span class="sxs-lookup"><span data-stu-id="c013d-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

     <span data-ttu-id="c013d-117">Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l' `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="c013d-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="c013d-118">Dans ce cas, la dernière instruction avant `End Function` doit être une `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="c013d-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="c013d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c013d-119">See also</span></span>

- [<span data-ttu-id="c013d-120">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="c013d-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="c013d-121">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="c013d-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="c013d-122">Page Compiler, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c013d-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
