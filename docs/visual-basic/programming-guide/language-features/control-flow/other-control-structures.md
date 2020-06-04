---
title: Autres structures de contrôle
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402016"
---
# <a name="other-control-structures-visual-basic"></a>Autres structures de contrôle (Visual Basic)
Visual Basic fournit des structures de contrôle qui vous permettent de supprimer une ressource ou de réduire le nombre de fois où vous devez répéter une référence d’objet.  
  
## <a name="usingend-using-construction"></a>Utilisation de... Terminer l’utilisation de la construction  
 La `Using...End Using` construction établit un bloc d’instructions dans lequel vous utilisez une ressource telle qu’une connexion SQL. Vous pouvez éventuellement acquérir la ressource avec l' `Using` instruction. Lorsque vous quittez le `Using` bloc, Visual Basic supprime automatiquement la ressource pour qu’elle soit disponible pour un autre code. La ressource doit être locale et jetable. Pour plus d’informations, consultez [using, instruction](../../../language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Avec... Terminer avec la construction  
 La `With...End With` construction vous permet de spécifier une référence d’objet une seule fois, puis d’exécuter une série d’instructions qui accèdent à ses membres. Cela peut simplifier votre code et améliorer les performances, car Visual Basic n’a pas à rétablir la référence pour chaque instruction qui y accède. Pour plus d’informations, consultez [avec... End With](../../../language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Workflow de contrôle](index.md)
- [Structures de décision](decision-structures.md)
- [Structures de boucle](loop-structures.md)
- [Structures de contrôle imbriquées](nested-control-structures.md)
- [Instruction using](../../../language-reference/statements/using-statement.md)
- [With...End With (instruction)](../../../language-reference/statements/with-end-with-statement.md)
