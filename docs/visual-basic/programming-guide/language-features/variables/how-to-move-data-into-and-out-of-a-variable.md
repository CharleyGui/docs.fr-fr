---
title: "Comment : placer des données dans et en dehors d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: fe19a6160623aa9ea867becdf7a15b51319abf45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410436"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Comment : placer des données dans et en dehors d'une variable (Visual Basic)

Vous stockez une valeur dans une variable en plaçant le nom de la variable sur le côté gauche d’une instruction d’assignation.

## <a name="putting-data-in-a-variable"></a>Ajout de données dans une variable

#### <a name="to-store-a-value-in-a-variable"></a>Pour stocker une valeur dans une variable

- Utilisez le nom de la variable sur le côté gauche d’une instruction d’assignation.

    L’exemple suivant définit la valeur de la variable `alpha` .

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la variable.

## <a name="getting-data-from-a-variable"></a>Obtention de données à partir d’une variable

Vous récupérez la valeur d’une variable en incluant le nom de la variable dans une expression.

#### <a name="to-retrieve-a-value-from-a-variable"></a>Pour récupérer une valeur d’une variable

- Utilisez le nom de la variable dans une expression. Vous pouvez utiliser une variable partout où vous pouvez utiliser une constante ou un littéral, sauf dans une expression qui définit la valeur d’une constante.

  \- ou -

- Utilisez le nom de variable après le signe égal ( `=` ) dans une instruction d’assignation.

  L’exemple suivant lit la valeur de la variable `startValue` , puis utilise la valeur de la variable `counter` dans une expression.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  La valeur de la variable participe à l’expression de la même manière qu’une constante, puis elle est stockée dans la variable ou la propriété à gauche de l’instruction d’assignation.

## <a name="see-also"></a>Voir aussi

- [Variables](index.md)
- [Déclaration de variable](variable-declaration.md)
- [Variables objets](object-variables.md)
