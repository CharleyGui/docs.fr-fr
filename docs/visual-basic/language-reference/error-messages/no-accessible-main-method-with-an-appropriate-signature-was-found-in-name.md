---
title: Aucune méthode 'Main' accessible avec une signature appropriée n'a été trouvée dans '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: e1f95484a153bdcac9543508b7f2708dc6b7d942
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160039"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="32fe1-102">BC30737 : aucune méthode’main’accessible avec une signature appropriée n’a été trouvée dans' \<name> '</span><span class="sxs-lookup"><span data-stu-id="32fe1-102">BC30737: No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>

<span data-ttu-id="32fe1-103">Les applications en ligne de commande doivent avoir un `Sub Main` défini.</span><span class="sxs-lookup"><span data-stu-id="32fe1-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="32fe1-104">`Main` doit être déclaré comme `Public Shared` s’il est défini dans une classe, ou comme `Public` s’il est défini dans un module.</span><span class="sxs-lookup"><span data-stu-id="32fe1-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>

 <span data-ttu-id="32fe1-105">**ID d’erreur :** BC30737</span><span class="sxs-lookup"><span data-stu-id="32fe1-105">**Error ID:** BC30737</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="32fe1-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="32fe1-106">To correct this error</span></span>

- <span data-ttu-id="32fe1-107">Définissez une `Public Sub Main` procédure pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="32fe1-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="32fe1-108">Déclarez-le comme `Shared` If et uniquement si vous le définissez à l’intérieur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="32fe1-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>

## <a name="see-also"></a><span data-ttu-id="32fe1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32fe1-109">See also</span></span>

- [<span data-ttu-id="32fe1-110">Structure d'un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32fe1-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="32fe1-111">Procédures</span><span class="sxs-lookup"><span data-stu-id="32fe1-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
