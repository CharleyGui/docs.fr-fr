---
title: 'Résolution des problèmes : Écouteurs de journalisation'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346857"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Dépannage : écouteurs de journalisation (Visual Basic)

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.  
  
 Pour déterminer les écouteurs de journalisation qui reçoivent ces messages, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 L’objet `Log` peut utiliser le filtrage de journal pour limiter la quantité d’informations qu’il journalise. Si les filtres sont mal configurés, les journaux peuvent contenir des informations incorrectes. Pour plus d'informations sur le filtrage, consultez [Procédure pas à pas : filtrage de la sortie de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Toutefois, si un journal est mal configuré, vous pouvez avoir besoin de davantage d’informations sur sa configuration actuelle. Vous pouvez accéder à ces informations grâce à la propriété avancée `TraceSource` du journal.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Pour déterminer les écouteurs de journalisation de l’objet Log dans le code  
  
1. Importez l’espace de noms <xref:System.Diagnostics> au début du fichier de code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Créez une fonction qui retourne une chaîne composée d’informations pour chacun des écouteurs du journal.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Passez la collection des écouteurs de la trace du journal à la fonction `GetListeners` et affichez la valeur de retour.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
