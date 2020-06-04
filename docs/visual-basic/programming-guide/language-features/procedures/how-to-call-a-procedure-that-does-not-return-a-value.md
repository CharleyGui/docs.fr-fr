---
title: 'Comment : appeler une procédure qui ne retourne pas de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 514d6e576b9b782387840ae04dcefa00de876aa9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388736"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic)
Une `Sub` procédure ne retourne pas de valeur au code appelant. Vous l’appelez explicitement avec une instruction d’appel autonome. Vous ne pouvez pas l’appeler en utilisant simplement son nom dans une expression.  
  
### <a name="to-call-a-sub-procedure"></a>Pour appeler une procédure Sub  
  
1. Spécifiez le nom de la `Sub` procédure.  
  
2. Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la `Sub` procédure définit les paramètres correspondants.  
  
     L’exemple suivant appelle la <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> fonction Visual Basic pour activer une fenêtre d’application. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>prend le titre de la fenêtre comme seul argument. Elle ne retourne pas de valeur au code appelant. Si un processus Notepad n’est pas en cours d’exécution, l’exemple lève une exception <xref:System.ArgumentException> . La `Shell` procédure suppose que les applications se trouvent dans les chemins d’accès spécifiés.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procédures](./index.md)
- [Sub, procédures](./sub-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [Guide pratique : créer une procédure](./how-to-create-a-procedure.md)
- [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
- [Comment : appeler un gestionnaire d'événements en Visual Basic](./how-to-call-an-event-handler.md)
