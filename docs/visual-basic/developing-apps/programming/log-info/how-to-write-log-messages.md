---
title: 'Procédure : écrire des messages de journal'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410047"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Comment : écrire des messages de journal (Visual Basic)

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur votre application. Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage.

Pour enregistrer des informations sur les exceptions, utilisez la méthode `My.Application.Log.WriteException`. Consultez [Guide pratique pour enregistrer des exceptions](how-to-log-exceptions.md).

## <a name="example"></a>Exemple

Cet exemple utilise la méthode `My.Application.Log.WriteEntry` pour écrire les informations de traçage.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Sécurité du .NET Framework

Vérifiez que les données que vous écrivez dans le journal n’incluent pas d’informations sensibles, comme des mots de passe utilisateur. Pour plus d’informations, consultez [Utilisation des journaux d’application](working-with-application-logs.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Utilisation des journaux des applications](working-with-application-logs.md)
- [Procédure : journaliser des exceptions](how-to-log-exceptions.md)
- [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md)
- [Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](walkthrough-changing-where-my-application-log-writes-information.md)
- [Procédure pas à pas : filtrage de la sortie de My.Application.Log](walkthrough-filtering-my-application-log-output.md)
