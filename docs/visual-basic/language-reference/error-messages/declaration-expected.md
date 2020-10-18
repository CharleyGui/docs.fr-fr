---
title: Déclaration attendue
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162698"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="67288-102">BC30188 : déclaration attendue</span><span class="sxs-lookup"><span data-stu-id="67288-102">BC30188: Declaration expected</span></span>

<span data-ttu-id="67288-103">Une instruction non déclarative, telle qu’une instruction d’assignation ou de boucle, se produit en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="67288-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="67288-104">Seules les déclarations sont autorisées en dehors des procédures.</span><span class="sxs-lookup"><span data-stu-id="67288-104">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="67288-105">Un élément de programmation est également déclaré sans mot clé de déclaration, tel que `Dim` ou `Const` .</span><span class="sxs-lookup"><span data-stu-id="67288-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="67288-106">**ID d’erreur :** BC30188</span><span class="sxs-lookup"><span data-stu-id="67288-106">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="67288-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="67288-107">To correct this error</span></span>

- <span data-ttu-id="67288-108">Déplacez l’instruction not Declarative dans le corps d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="67288-108">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="67288-109">Commencez la déclaration par un mot clé de déclaration approprié.</span><span class="sxs-lookup"><span data-stu-id="67288-109">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="67288-110">Assurez-vous qu’un mot clé de déclaration n’est pas mal orthographié.</span><span class="sxs-lookup"><span data-stu-id="67288-110">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="67288-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67288-111">See also</span></span>

- [<span data-ttu-id="67288-112">Procédures</span><span class="sxs-lookup"><span data-stu-id="67288-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="67288-113">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="67288-113">Dim Statement</span></span>](../statements/dim-statement.md)
