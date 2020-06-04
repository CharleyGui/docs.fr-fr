---
title: "'<keyword>' est valide uniquement dans une méthode d'instance"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397400"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="603f7-102">'\<keyword>' est valide uniquement dans une méthode d'instance</span><span class="sxs-lookup"><span data-stu-id="603f7-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="603f7-103">Les `Me` `MyClass` `MyBase` Mots clés, et font référence à des instances de classe spécifiques.</span><span class="sxs-lookup"><span data-stu-id="603f7-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="603f7-104">Vous ne pouvez pas les utiliser dans `Function` une `Sub` procédure ou partagée.</span><span class="sxs-lookup"><span data-stu-id="603f7-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="603f7-105">**ID d’erreur :** BC30043</span><span class="sxs-lookup"><span data-stu-id="603f7-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="603f7-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="603f7-106">To correct this error</span></span>  
  
- <span data-ttu-id="603f7-107">Supprimez le mot clé de la procédure ou supprimez le `Shared` mot clé de la déclaration de procédure.</span><span class="sxs-lookup"><span data-stu-id="603f7-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603f7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="603f7-108">See also</span></span>

- [<span data-ttu-id="603f7-109">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="603f7-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="603f7-110">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="603f7-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="603f7-111">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="603f7-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
