---
title: L'objet ou la classe ne prend pas en charge le jeu d'événements
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409359"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="34f48-102">L'objet ou la classe ne prend pas en charge le jeu d'événements</span><span class="sxs-lookup"><span data-stu-id="34f48-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="34f48-103">Vous avez essayé d’utiliser une `WithEvents` variable avec un composant qui ne peut pas fonctionner en tant que source d’événement pour le jeu d’événements spécifié.</span><span class="sxs-lookup"><span data-stu-id="34f48-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="34f48-104">Par exemple, vous souhaitez recevoir les événements d’un objet, puis créer un autre objet qui est `Implements` le premier objet.</span><span class="sxs-lookup"><span data-stu-id="34f48-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="34f48-105">Vous pourriez penser que vous pourriez recevoir les événements de l’objet implémenté, ce n’est pas toujours le cas.</span><span class="sxs-lookup"><span data-stu-id="34f48-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="34f48-106">`Implements`implémente uniquement une interface pour les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="34f48-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="34f48-107">`WithEvents`n’est pas pris en charge pour Private `UserControls` , car les informations de type nécessaires pour déclencher le `ObjectEvent` n’est pas disponible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="34f48-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34f48-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="34f48-108">To correct this error</span></span>  
  
1. <span data-ttu-id="34f48-109">Vous ne pouvez pas recevoir d’événements pour un composant qui n’a pas d’événements sources.</span><span class="sxs-lookup"><span data-stu-id="34f48-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f48-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f48-110">See also</span></span>

- [<span data-ttu-id="34f48-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="34f48-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="34f48-112">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="34f48-112">Implements Statement</span></span>](../statements/implements-statement.md)
