---
title: La variable '<variablename>' est utilisée avant qu'une valeur ne lui ait été assignée
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 6db8626701267f2051b289b267e7b2d9da51c283
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162217"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="ef199-102">COMPILATION BC42104 : la variable' \<variablename> 'est utilisée avant qu’une valeur ne lui ait été assignée</span><span class="sxs-lookup"><span data-stu-id="ef199-102">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="ef199-103">La variable' \<variablename> 'est utilisée avant qu’une valeur ne lui ait été assignée.</span><span class="sxs-lookup"><span data-stu-id="ef199-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="ef199-104">Cela peut provoquer une exception de référence null au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ef199-104">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="ef199-105">Une application a au moins un chemin d’accès possible via son code qui lit une variable avant qu’une valeur ne lui soit assignée.</span><span class="sxs-lookup"><span data-stu-id="ef199-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="ef199-106">Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données.</span><span class="sxs-lookup"><span data-stu-id="ef199-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="ef199-107">Pour un type de données référence, cette valeur par défaut est [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="ef199-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="ef199-108">La lecture d’une variable de référence qui a la valeur `Nothing` peut provoquer une <xref:System.NullReferenceException> dans certaines circonstances.</span><span class="sxs-lookup"><span data-stu-id="ef199-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="ef199-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="ef199-109">By default, this message is a warning.</span></span> <span data-ttu-id="ef199-110">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ef199-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="ef199-111">**ID d’erreur :** COMPILATION BC42104</span><span class="sxs-lookup"><span data-stu-id="ef199-111">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ef199-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ef199-112">To correct this error</span></span>

- <span data-ttu-id="ef199-113">Vérifiez votre logique de workflow de contrôle et assurez-vous que la variable a une valeur valide avant que le contrôle ne passe à une instruction qui la lit.</span><span class="sxs-lookup"><span data-stu-id="ef199-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="ef199-114">Pour garantir que la variable a toujours une valeur valide, vous pouvez l’initialiser dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="ef199-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="ef199-115">Consultez « initialisation » dans l' [instruction Dim](../statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ef199-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef199-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef199-116">See also</span></span>

- [<span data-ttu-id="ef199-117">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="ef199-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="ef199-118">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="ef199-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="ef199-119">Dépannage des variables</span><span class="sxs-lookup"><span data-stu-id="ef199-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
