---
title: 'Procédure : journaliser des exceptions'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352089"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Guide pratique pour enregistrer des exceptions en Visual Basic

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les exceptions qui se produisent dans votre application. Ces exemples montrent comment utiliser la méthode `My.Application.Log.WriteException` pour enregistrer des exceptions que vous interceptez explicitement et des exceptions qui ne sont pas gérées.  
  
 Pour enregistrer des informations de traçage, utilisez la méthode `My.Application.Log.WriteEntry`. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>Pour enregistrer une exception gérée  
  
1. Créez la méthode qui génère les informations sur l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Utilisez un bloc `Try...Catch` pour intercepter l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Placez le code susceptible de générer une exception dans le bloc `Try`.  
  
     Supprimez les commentaires des lignes `Dim` et `MsgBox` pour déclencher une exception <xref:System.NullReferenceException>.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. Dans le bloc `Catch`, utilisez la méthode `My.Application.Log.WriteException` pour écrire les informations sur l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     L’exemple suivant montre le code complet permettant d’enregistrer une exception gérée.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>Pour enregistrer une exception non gérée  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **projet** , choisissez **Propriétés**.  
  
2. Cliquez sur l’onglet **Application** .  
  
3. Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.  
  
     Le fichier ApplicationEvents.vb s’ouvre.  
  
4. Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code. Dans le menu **Général** , choisissez **Événements MyApplication**.  
  
5. Dans le menu **Déclarations**, choisissez **UnhandledException**.  
  
     L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> avant l’exécution de l’application principale.  
  
6. Ajoutez la méthode `My.Application.Log.WriteException` au gestionnaire d’événements `UnhandledException` .  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     L’exemple suivant montre le code complet permettant d’enregistrer une exception non gérée.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Procédure : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
