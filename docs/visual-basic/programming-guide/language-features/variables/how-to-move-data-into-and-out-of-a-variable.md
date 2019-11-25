---
title: "Comment : placer des données dans et en dehors d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bc5a7377a5e2e4c7ebe7291fd5f0093c4d6e996d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346900"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Comment : placer des données dans et en dehors d'une variable (Visual Basic)

You store a value in a variable by putting the variable name on the left side of an assignment statement.

## <a name="putting-data-in-a-variable"></a>Putting Data in a Variable

#### <a name="to-store-a-value-in-a-variable"></a>To store a value in a variable

- Use the variable name on the left side of an assignment statement.

    The following example sets the value of the variable `alpha`.

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    The value generated on the right side of the assignment statement is stored in the variable.

## <a name="getting-data-from-a-variable"></a>Getting Data from a Variable

You retrieve a variable's value by including the variable name in an expression.

#### <a name="to-retrieve-a-value-from-a-variable"></a>To retrieve a value from a variable

- Use the variable name in an expression. You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.

  \- ou -

- Use the variable name following the equal (`=`) sign in an assignment statement.

  The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.

## <a name="see-also"></a>Voir aussi

- [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
