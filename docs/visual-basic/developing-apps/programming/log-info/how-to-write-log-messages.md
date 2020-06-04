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
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="97a9d-102">Comment : écrire des messages de journal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97a9d-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="97a9d-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur votre application.</span><span class="sxs-lookup"><span data-stu-id="97a9d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="97a9d-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="97a9d-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="97a9d-105">Pour enregistrer des informations sur les exceptions, utilisez la méthode `My.Application.Log.WriteException`. Consultez [Guide pratique pour enregistrer des exceptions](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="97a9d-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="97a9d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="97a9d-106">Example</span></span>

<span data-ttu-id="97a9d-107">Cet exemple utilise la méthode `My.Application.Log.WriteEntry` pour écrire les informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="97a9d-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="97a9d-108">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97a9d-108">.NET Framework Security</span></span>

<span data-ttu-id="97a9d-109">Vérifiez que les données que vous écrivez dans le journal n’incluent pas d’informations sensibles, comme des mots de passe utilisateur.</span><span class="sxs-lookup"><span data-stu-id="97a9d-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="97a9d-110">Pour plus d’informations, consultez [Utilisation des journaux d’application](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="97a9d-110">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97a9d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a9d-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="97a9d-112">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="97a9d-112">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="97a9d-113">Procédure : journaliser des exceptions</span><span class="sxs-lookup"><span data-stu-id="97a9d-113">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="97a9d-114">Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="97a9d-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="97a9d-115">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="97a9d-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="97a9d-116">Procédure pas à pas : filtrage de la sortie de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="97a9d-116">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)
