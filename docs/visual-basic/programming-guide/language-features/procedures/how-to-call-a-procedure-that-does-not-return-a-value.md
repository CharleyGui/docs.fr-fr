---
title: 'Comment : appeler une procédure qui ne retourne pas de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340956"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic)
Une procédure `Sub` ne retourne pas de valeur au code appelant. Vous l’appelez explicitement avec une instruction d’appel autonome. Vous ne pouvez pas l’appeler en utilisant simplement son nom dans une expression.  
  
### <a name="to-call-a-sub-procedure"></a>Pour appeler une procédure Sub  
  
1. Spécifiez le nom de la procédure `Sub`.  
  
2. Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la procédure `Sub` définit les paramètres correspondants.  
  
     L’exemple suivant appelle la fonction <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> Visual Basic pour activer une fenêtre d’application. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> prend le titre de la fenêtre comme seul argument. Elle ne retourne pas de valeur au code appelant. Si un processus Notepad n’est pas en cours d’exécution, l’exemple lève une <xref:System.ArgumentException>. La procédure `Shell` suppose que les applications se trouvent dans les chemins d’accès spécifiés.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Guide pratique : créer une procédure](./how-to-create-a-procedure.md)
- [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
- [Comment : appeler un gestionnaire d’événements dans Visual Basic](./how-to-call-an-event-handler.md)
