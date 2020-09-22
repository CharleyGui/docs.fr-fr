---
title: La structure '<structurename>' doit contenir au moins une variable membre d'instance ou au moins une déclaration d'événement d'instance non marquée comme 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a350940cf052aa8fbee4a1e3c61cbeaa4e37408a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870582"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="a0552-102">La structure '\<structurename>' doit contenir au moins une variable membre d'instance ou au moins une déclaration d'événement d'instance non marquée comme 'Custom'.</span><span class="sxs-lookup"><span data-stu-id="a0552-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="a0552-103">Une définition de structure n’inclut pas de variables non partagées ou d’événements non personnalisés non partagés.</span><span class="sxs-lookup"><span data-stu-id="a0552-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="a0552-104">Chaque structure doit avoir une variable ou un événement qui s’applique à chaque instance spécifique (non partagée) au lieu de toutes les instances collectivement ([partagées](../modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="a0552-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="a0552-105">Les constantes, les propriétés et les procédures non partagées ne répondent pas à cette exigence.</span><span class="sxs-lookup"><span data-stu-id="a0552-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="a0552-106">En outre, s’il n’existe aucune variable non partagée et un seul événement non partagé, cet événement ne peut pas être un `Custom` événement.</span><span class="sxs-lookup"><span data-stu-id="a0552-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="a0552-107">**ID d’erreur :** BC30941</span><span class="sxs-lookup"><span data-stu-id="a0552-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0552-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a0552-108">To correct this error</span></span>  
  
- <span data-ttu-id="a0552-109">Définissez au moins une variable ou un événement qui n’est pas `Shared` .</span><span class="sxs-lookup"><span data-stu-id="a0552-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="a0552-110">Si vous ne définissez qu’un seul événement, celui-ci doit être non personnalisé et non partagé.</span><span class="sxs-lookup"><span data-stu-id="a0552-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0552-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0552-111">See also</span></span>

- [<span data-ttu-id="a0552-112">Structures</span><span class="sxs-lookup"><span data-stu-id="a0552-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a0552-113">Procédure : Déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="a0552-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a0552-114">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="a0552-114">Structure Statement</span></span>](../statements/structure-statement.md)
