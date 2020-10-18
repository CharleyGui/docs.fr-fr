---
title: "'<keyword>' est valide uniquement dans une méthode d'instance"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163322"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="4e794-102">BC30043 : ' \<keyword> 'est valide uniquement dans une méthode d’instance</span><span class="sxs-lookup"><span data-stu-id="4e794-102">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="4e794-103">Les `Me` `MyClass` `MyBase` Mots clés, et font référence à des instances de classe spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4e794-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="4e794-104">Vous ne pouvez pas les utiliser dans `Function` une `Sub` procédure ou partagée.</span><span class="sxs-lookup"><span data-stu-id="4e794-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="4e794-105">*ID d’erreur :*\* BC30043</span><span class="sxs-lookup"><span data-stu-id="4e794-105">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4e794-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4e794-106">To correct this error</span></span>

- <span data-ttu-id="4e794-107">Supprimez le mot clé de la procédure ou supprimez le `Shared` mot clé de la déclaration de procédure.</span><span class="sxs-lookup"><span data-stu-id="4e794-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e794-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e794-108">See also</span></span>

- [<span data-ttu-id="4e794-109">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="4e794-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="4e794-110">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="4e794-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="4e794-111">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="4e794-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
