---
title: L’utilisation de l’instance par défaut d’une classe dans le constructeur de classe pourrait entraîner des appels récurrents infinis
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100319"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>L’utilisation de l’instance par défaut d’une classe dans le constructeur de classe pourrait entraîner des appels récurrents infinis

Une instance par défaut d’une classe a été utilisée dans le constructeur de la classe. Cela peut entraîner un appel récurrent infini, également appelé « boucle infinie ».  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez l’instance par défaut du constructeur de la classe.  
  
## <a name="see-also"></a>Voir aussi

- [Constructeurs](../programming-guide/concepts/object-oriented-programming.md#constructors)
