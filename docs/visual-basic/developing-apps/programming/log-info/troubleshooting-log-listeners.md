---
title: 'Résolution des problèmes : Écouteurs de journalisation'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 8d2d8294d9e9bb42d72fe4f6c37bf846bd644907
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398316"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="a88fb-102">Dépannage : écouteurs de journalisation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a88fb-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="a88fb-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a88fb-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="a88fb-104">Pour déterminer les écouteurs de journalisation qui reçoivent ces messages, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="a88fb-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="a88fb-105">L’objet `Log` peut utiliser le filtrage de journal pour limiter la quantité d’informations qu’il journalise.</span><span class="sxs-lookup"><span data-stu-id="a88fb-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="a88fb-106">Si les filtres sont mal configurés, les journaux peuvent contenir des informations incorrectes.</span><span class="sxs-lookup"><span data-stu-id="a88fb-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="a88fb-107">Pour plus d'informations sur le filtrage, consultez [Procédure pas à pas : filtrage de la sortie de My.Application.Log](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="a88fb-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="a88fb-108">Toutefois, si un journal est mal configuré, vous pouvez avoir besoin de davantage d’informations sur sa configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="a88fb-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="a88fb-109">Vous pouvez accéder à ces informations grâce à la propriété avancée `TraceSource` du journal.</span><span class="sxs-lookup"><span data-stu-id="a88fb-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="a88fb-110">Pour déterminer les écouteurs de journalisation de l’objet Log dans le code</span><span class="sxs-lookup"><span data-stu-id="a88fb-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="a88fb-111">Importez l’espace de noms <xref:System.Diagnostics> au début du fichier de code.</span><span class="sxs-lookup"><span data-stu-id="a88fb-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="a88fb-112">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a88fb-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="a88fb-113">Créez une fonction qui retourne une chaîne composée d’informations pour chacun des écouteurs du journal.</span><span class="sxs-lookup"><span data-stu-id="a88fb-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="a88fb-114">Passez la collection des écouteurs de la trace du journal à la fonction `GetListeners` et affichez la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a88fb-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="a88fb-115">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="a88fb-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88fb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a88fb-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="a88fb-117">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="a88fb-117">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="a88fb-118">Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="a88fb-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
