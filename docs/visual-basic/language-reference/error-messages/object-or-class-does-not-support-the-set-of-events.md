---
title: L'objet ou la classe ne prend pas en charge le jeu d'événements
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873652"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>L'objet ou la classe ne prend pas en charge le jeu d'événements

Vous avez essayé d’utiliser une `WithEvents` variable avec un composant qui ne peut pas fonctionner en tant que source d’événement pour le jeu d’événements spécifié. Par exemple, vous souhaitez recevoir les événements d’un objet, puis créer un autre objet qui est `Implements` le premier objet. Vous pourriez penser que vous pourriez recevoir les événements de l’objet implémenté, ce n’est pas toujours le cas. `Implements` implémente uniquement une interface pour les méthodes et les propriétés. `WithEvents` n’est pas pris en charge pour Private `UserControls` , car les informations de type nécessaires pour déclencher le `ObjectEvent` n’est pas disponible au moment de l’exécution.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vous ne pouvez pas recevoir d’événements pour un composant qui n’a pas d’événements sources.  
  
## <a name="see-also"></a>Voir aussi

- [WithEvents](../modifiers/withevents.md)
- [Implements, instruction](../statements/implements-statement.md)
