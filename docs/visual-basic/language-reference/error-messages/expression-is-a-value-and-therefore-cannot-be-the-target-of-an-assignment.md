---
title: Cette expression est une valeur et ne peut donc pas être la cible d'une assignation
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513036"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Cette expression est une valeur et ne peut donc pas être la cible d'une assignation

Une instruction tente d’affecter une valeur à une expression. Vous pouvez assigner une valeur uniquement à une variable, une propriété ou un élément de tableau accessible en écriture au moment de l’exécution. L’exemple suivant illustre la façon dont cette erreur peut se produire.

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

Des exemples similaires peuvent s’appliquer aux propriétés et aux éléments de tableau.

**Accès indirect.** L’accès indirect via un type valeur peut également générer cette erreur. Prenons l’exemple de code suivant, qui tente de définir la valeur <xref:System.Drawing.Point> de en y accédant indirectement <xref:System.Windows.Forms.Control.Location%2A>par le biais de.

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

La dernière instruction de l’exemple précédent échoue, car elle crée uniquement une allocation temporaire pour <xref:System.Drawing.Point> la structure retournée <xref:System.Windows.Forms.Control.Location%2A> par la propriété. Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction. Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A>, ce qui crée une allocation plus permanente pour <xref:System.Drawing.Point> la structure. L’exemple suivant montre le code qui peut remplacer la dernière instruction de l’exemple précédent.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**ID d’erreur:** BC30068

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable, une propriété ou un élément de tableau accessible en écriture unique.

- Si l’instruction fait un accès indirect par le biais d’un type valeur (généralement une structure), créez une variable qui contiendra le type valeur.

- Assignez la structure appropriée (ou un autre type de valeur) à la variable.

- Utilisez la variable pour accéder à la propriété afin de lui assigner une valeur.

## <a name="see-also"></a>Voir aussi

- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
- [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
