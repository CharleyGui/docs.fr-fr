---
title: 'Comment : valider des chaînes qui représentent des dates ou des heures'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348414"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Comment : valider des chaînes qui représentent des dates ou des heures (Visual Basic)
L’exemple de code suivant définit une valeur `Boolean` qui indique si une chaîne représente une date ou une heure valide.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Remplacez `("01/01/03")` et `"9:30 PM"` par la date et l’heure que vous souhaitez valider. Vous pouvez remplacer la chaîne par une autre chaîne codée en dur, par une variable `String` ou par une méthode qui retourne une chaîne, telle que `InputBox`.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Utilisez cette méthode pour valider la chaîne avant d’essayer de convertir le `String` en une variable `DateTime`. En vérifiant d’abord la date ou l’heure, vous pouvez éviter de générer une exception au moment de l’exécution.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
