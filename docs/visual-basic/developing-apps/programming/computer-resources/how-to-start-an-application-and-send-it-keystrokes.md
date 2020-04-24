---
title: 'Comment : démarrer une application et lui envoyer des séquences de touches-Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72919389"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Comment : démarrer une application et lui envoyer des séquences de touches (Visual Basic)

Cet exemple utilise la <xref:Microsoft.VisualBasic.Interaction.Shell%2A> méthode pour démarrer l’application Notepad, puis imprime une phrase en envoyant des séquences de touches à l’aide de la méthode [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) .

## <a name="example"></a>Exemple

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Programmation fiable

Une <xref:System.ArgumentException> exception est levée si une application avec l’identificateur de processus demandé est introuvable.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework

L’appel à la fonction `Shell` nécessite une confiance totale (classe <xref:System.Security.SecurityException>).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
