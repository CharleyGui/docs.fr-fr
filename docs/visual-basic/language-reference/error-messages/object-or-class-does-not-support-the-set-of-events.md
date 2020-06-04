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
# <a name="object-or-class-does-not-support-the-set-of-events"></a>L'objet ou la classe ne prend pas en charge le jeu d'événements
Vous avez essayé d’utiliser une `WithEvents` variable avec un composant qui ne peut pas fonctionner en tant que source d’événement pour le jeu d’événements spécifié. Par exemple, vous souhaitez recevoir les événements d’un objet, puis créer un autre objet qui est `Implements` le premier objet. Vous pourriez penser que vous pourriez recevoir les événements de l’objet implémenté, ce n’est pas toujours le cas. `Implements`implémente uniquement une interface pour les méthodes et les propriétés. `WithEvents`n’est pas pris en charge pour Private `UserControls` , car les informations de type nécessaires pour déclencher le `ObjectEvent` n’est pas disponible au moment de l’exécution.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vous ne pouvez pas recevoir d’événements pour un composant qui n’a pas d’événements sources.  
  
## <a name="see-also"></a>Voir aussi

- [WithEvents](../modifiers/withevents.md)
- [Implements, instruction](../statements/implements-statement.md)
