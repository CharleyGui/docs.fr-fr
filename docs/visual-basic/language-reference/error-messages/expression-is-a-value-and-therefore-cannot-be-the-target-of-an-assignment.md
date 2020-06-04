---
title: Cette expression est une valeur et ne peut donc pas être la cible d'une assignation
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409505"
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

**Accès indirect.** L’accès indirect via un type valeur peut également générer cette erreur. Prenons l’exemple de code suivant, qui tente de définir la valeur de <xref:System.Drawing.Point> en y accédant indirectement par le biais de <xref:System.Windows.Forms.Control.Location%2A> .

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

La dernière instruction de l’exemple précédent échoue, car elle crée uniquement une allocation temporaire pour la <xref:System.Drawing.Point> structure retournée par la <xref:System.Windows.Forms.Control.Location%2A> propriété. Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction. Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A> , ce qui crée une allocation plus permanente pour la <xref:System.Drawing.Point> structure. L’exemple suivant montre le code qui peut remplacer la dernière instruction de l’exemple précédent.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**ID d’erreur :** BC30068

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable, une propriété ou un élément de tableau accessible en écriture unique.

- Si l’instruction fait un accès indirect par le biais d’un type valeur (généralement une structure), créez une variable qui contiendra le type valeur.

- Assignez la structure appropriée (ou un autre type de valeur) à la variable.

- Utilisez la variable pour accéder à la propriété afin de lui assigner une valeur.

## <a name="see-also"></a>Voir aussi

- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instructions](../../programming-guide/language-features/statements.md)
- [Procédures de dépannage](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
