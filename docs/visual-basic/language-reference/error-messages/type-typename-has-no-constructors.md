---
title: Le type '<typename>' n'a aucun constructeur
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161177"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="20984-102">BC30251 : le type' \<typename> 'n’a pas de constructeurs</span><span class="sxs-lookup"><span data-stu-id="20984-102">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="20984-103">Un type ne prend pas en charge un appel à `Sub New()`.</span><span class="sxs-lookup"><span data-stu-id="20984-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="20984-104">L'une des causes probables est un fichier compilateur ou binaire endommagé.</span><span class="sxs-lookup"><span data-stu-id="20984-104">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="20984-105">**ID d’erreur :** BC30251</span><span class="sxs-lookup"><span data-stu-id="20984-105">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="20984-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="20984-106">To correct this error</span></span>

1. <span data-ttu-id="20984-107">Si le type se trouve dans un projet différent ou dans un fichier référencé, réinstallez le projet ou le fichier.</span><span class="sxs-lookup"><span data-stu-id="20984-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="20984-108">Si le type se trouve dans le même projet, recompilez l'assembly contenant le type.</span><span class="sxs-lookup"><span data-stu-id="20984-108">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="20984-109">Si l’erreur se reproduit, réinstallez le compilateur Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20984-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="20984-110">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="20984-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="20984-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20984-111">See also</span></span>

- [<span data-ttu-id="20984-112">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="20984-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="20984-113">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="20984-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
