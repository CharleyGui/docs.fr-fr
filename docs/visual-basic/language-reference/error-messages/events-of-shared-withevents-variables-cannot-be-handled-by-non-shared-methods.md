---
title: Les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: d519463e036de215143efad5be3745484ac17d82
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874291"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="98dc6-102">Les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées</span><span class="sxs-lookup"><span data-stu-id="98dc6-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>

<span data-ttu-id="98dc6-103">Une variable déclarée avec le `Shared` modificateur est une variable partagée.</span><span class="sxs-lookup"><span data-stu-id="98dc6-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="98dc6-104">Une variable partagée identifie exactement un emplacement de stockage.</span><span class="sxs-lookup"><span data-stu-id="98dc6-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="98dc6-105">Une variable déclarée avec le `WithEvents` modificateur déclare que le type auquel la variable appartient gère l’ensemble des événements déclenchés par la variable.</span><span class="sxs-lookup"><span data-stu-id="98dc6-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="98dc6-106">Quand une valeur est assignée à la variable, la propriété créée par la `WithEvents` déclaration décroche un gestionnaire d’événements existant et raccorde le nouveau gestionnaire d’événements via la `Add` méthode.</span><span class="sxs-lookup"><span data-stu-id="98dc6-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="98dc6-107">**ID d’erreur :** BC30594</span><span class="sxs-lookup"><span data-stu-id="98dc6-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98dc6-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="98dc6-108">To correct this error</span></span>  
  
- <span data-ttu-id="98dc6-109">Déclarez votre gestionnaire d’événements `Shared` .</span><span class="sxs-lookup"><span data-stu-id="98dc6-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98dc6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98dc6-110">See also</span></span>

- [<span data-ttu-id="98dc6-111">Partagé</span><span class="sxs-lookup"><span data-stu-id="98dc6-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="98dc6-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="98dc6-112">WithEvents</span></span>](../modifiers/withevents.md)
