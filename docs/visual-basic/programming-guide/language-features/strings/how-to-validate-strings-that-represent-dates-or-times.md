---
title: 'Comment : valider des chaînes qui représentent des dates ou des heures'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f3654894e274404410179dab04422e20f6040440
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072598"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Comment : valider des chaînes qui représentent des dates ou des heures (Visual Basic)

L’exemple de code suivant définit une `Boolean` valeur qui indique si une chaîne représente une date ou une heure valide.  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Compiler le code  

 Remplacez `("01/01/03")` et `"9:30 PM"` par la date et l’heure que vous souhaitez valider. Vous pouvez remplacer la chaîne par une autre chaîne codée en dur, par une `String` variable ou par une méthode qui retourne une chaîne, telle que `InputBox` .  
  
## <a name="robust-programming"></a>Programmation fiable  

 Utilisez cette méthode pour valider la chaîne avant d’essayer de convertir `String` en une `DateTime` variable. En vérifiant d’abord la date ou l’heure, vous pouvez éviter de générer une exception au moment de l’exécution.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Validation de chaînes en Visual Basic](validating-strings.md)
