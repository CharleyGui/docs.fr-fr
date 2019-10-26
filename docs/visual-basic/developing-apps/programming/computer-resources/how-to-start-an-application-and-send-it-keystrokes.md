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
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919389"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="84c33-102">Comment : démarrer une application et lui envoyer des séquences de touches (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84c33-102">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="84c33-103">Cet exemple utilise la méthode <xref:Microsoft.VisualBasic.Interaction.Shell%2A> pour démarrer l’application Notepad, puis imprime une phrase en envoyant des séquences de touches à l’aide de la méthode [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) .</span><span class="sxs-lookup"><span data-stu-id="84c33-103">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="84c33-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="84c33-104">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="84c33-105">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="84c33-105">Robust programming</span></span>

<span data-ttu-id="84c33-106">Une exception <xref:System.ArgumentException> est levée si une application avec l’identificateur de processus demandé est introuvable.</span><span class="sxs-lookup"><span data-stu-id="84c33-106">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="84c33-107">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84c33-107">.NET Framework Security</span></span>

<span data-ttu-id="84c33-108">L’appel à la fonction `Shell` nécessite une confiance totale (classe <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="84c33-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="84c33-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84c33-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
