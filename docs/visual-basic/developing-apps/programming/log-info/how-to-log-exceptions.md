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
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="f9983-102">Guide pratique pour enregistrer des exceptions en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9983-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="f9983-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les exceptions qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f9983-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="f9983-104">Ces exemples montrent comment utiliser la méthode `My.Application.Log.WriteException` pour enregistrer des exceptions que vous interceptez explicitement et des exceptions qui ne sont pas gérées.</span><span class="sxs-lookup"><span data-stu-id="f9983-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="f9983-105">Pour enregistrer des informations de traçage, utilisez la méthode `My.Application.Log.WriteEntry`.</span><span class="sxs-lookup"><span data-stu-id="f9983-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="f9983-106">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="f9983-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="f9983-107">Pour enregistrer une exception gérée</span><span class="sxs-lookup"><span data-stu-id="f9983-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="f9983-108">Créez la méthode qui génère les informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="f9983-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="f9983-109">Utilisez un bloc `Try...Catch` pour intercepter l’exception.</span><span class="sxs-lookup"><span data-stu-id="f9983-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="f9983-110">Placez le code susceptible de générer une exception dans le bloc `Try`.</span><span class="sxs-lookup"><span data-stu-id="f9983-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="f9983-111">Supprimez les commentaires des lignes `Dim` et `MsgBox` pour déclencher une exception <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="f9983-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="f9983-112">Dans le bloc `Catch`, utilisez la méthode `My.Application.Log.WriteException` pour écrire les informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="f9983-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="f9983-113">L’exemple suivant montre le code complet permettant d’enregistrer une exception gérée.</span><span class="sxs-lookup"><span data-stu-id="f9983-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="f9983-114">Pour enregistrer une exception non gérée</span><span class="sxs-lookup"><span data-stu-id="f9983-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="f9983-115">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="f9983-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f9983-116">Dans le menu **projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9983-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="f9983-117">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="f9983-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="f9983-118">Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="f9983-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="f9983-119">Le fichier ApplicationEvents.vb s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="f9983-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="f9983-120">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="f9983-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="f9983-121">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="f9983-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="f9983-122">Dans le menu **Déclarations**, choisissez **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="f9983-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="f9983-123">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> avant l’exécution de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="f9983-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="f9983-124">Ajoutez la méthode `My.Application.Log.WriteException` au gestionnaire d’événements `UnhandledException` .</span><span class="sxs-lookup"><span data-stu-id="f9983-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="f9983-125">L’exemple suivant montre le code complet permettant d’enregistrer une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="f9983-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f9983-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9983-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="f9983-127">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="f9983-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="f9983-128">Procédure : écrire des messages de journal</span><span class="sxs-lookup"><span data-stu-id="f9983-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="f9983-129">Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f9983-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="f9983-130">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f9983-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
