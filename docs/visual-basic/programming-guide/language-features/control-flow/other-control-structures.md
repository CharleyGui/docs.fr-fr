---
title: Autres structures de contrôle
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348130"
---
# <a name="other-control-structures-visual-basic"></a>Autres structures de contrôle (Visual Basic)
Visual Basic fournit des structures de contrôle qui vous permettent de supprimer une ressource ou de réduire le nombre de fois où vous devez répéter une référence d’objet.  
  
## <a name="usingend-using-construction"></a>Utilisation de... Terminer l’utilisation de la construction  
 La construction `Using...End Using` établit un bloc d’instructions dans lequel vous utilisez une ressource telle qu’une connexion SQL. Vous pouvez éventuellement acquérir la ressource avec l’instruction `Using`. Lorsque vous quittez le bloc `Using`, Visual Basic supprime automatiquement la ressource pour qu’elle soit disponible pour un autre code. La ressource doit être locale et jetable. Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Avec... Terminer avec la construction  
 La construction `With...End With` vous permet de spécifier une référence d’objet une seule fois, puis d’exécuter une série d’instructions qui accèdent à ses membres. Cela peut simplifier votre code et améliorer les performances, car Visual Basic n’a pas à rétablir la référence pour chaque instruction qui y accède. Pour plus d’informations, consultez [avec... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using (instruction)](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With (instruction)](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
