---
title: Structures de décision
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: aac9844240defc5a21a3f4e6090fa8f49e6348a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403513"
---
# <a name="decision-structures-visual-basic"></a>Structures de décision (Visual Basic)
Visual Basic vous permet de tester des conditions et d’effectuer différentes opérations en fonction des résultats de ce test. Vous pouvez tester si une condition est true ou false, pour différentes valeurs d’une expression ou pour différentes exceptions générées lorsque vous exécutez une série d’instructions.  
  
 L’illustration suivante montre une structure de décision qui teste la présence d’une condition ayant la valeur true et qui effectue des actions différentes selon qu’il s’agit d’une valeur true ou false.  
  
 ![Organigramme d’une if... Puis... Construction Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If... Puis... Construction Else  
 `If...Then...Else`les constructions vous permettent de tester une ou plusieurs conditions et d’exécuter une ou plusieurs instructions en fonction de chaque condition. Vous pouvez tester des conditions et prendre des mesures de la manière suivante :  
  
- Exécuter une ou plusieurs instructions si une condition est`True`  
  
- Exécuter une ou plusieurs instructions si une condition est`False`  
  
- Exécuter des instructions si une condition est `True` et d’autres si elle est`False`  
  
- Tester une condition supplémentaire si une condition antérieure est`False`  
  
 La structure de contrôle qui offre toutes ces possibilités est le [If... Puis... Instruction Else](../../../language-reference/statements/if-then-else-statement.md). Vous pouvez utiliser une version sur une seule ligne si vous n’avez qu’un seul test et une seule instruction à exécuter. Si vous avez un ensemble plus complexe de conditions et d’actions, vous pouvez utiliser la version sur plusieurs lignes.  
  
## <a name="selectcase-construction"></a>Sélectionner... Construction de cas  
 La `Select...Case` construction vous permet d’évaluer une expression une fois et d’exécuter différents jeux d’instructions en fonction de différentes valeurs possibles. Pour plus d’informations, consultez [Select... Instruction case](../../../language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Essayer... Catch... Finalisation de la construction  
 `Try...Catch...Finally`les constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’une de vos instructions provoque une exception. Vous pouvez effectuer différentes actions pour différentes exceptions. Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter la `Try...Catch...Finally` construction entière, indépendamment de ce qui se produit. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez `If` dans une `If...Then...Else` construction, toutes les instances de,,, `If` `Then` `ElseIf` `Else` et `End If` de la construction sont mises en surbrillance. Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + haut.  
  
## <a name="see-also"></a>Voir aussi

- [Workflow de contrôle](index.md)
- [Structures de boucle](loop-structures.md)
- [Autres structures de contrôle](other-control-structures.md)
- [Structures de contrôle imbriquées](nested-control-structures.md)
- [If, opérateur](../../../language-reference/operators/if-operator.md)
