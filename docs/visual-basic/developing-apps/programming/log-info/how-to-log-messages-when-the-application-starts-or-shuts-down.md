---
title: 'Procédure : enregistrer des messages quand l’application démarre ou s’arrête'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: ac5fb17e527bcbcb55f98ec0ced06c152555ce6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410073"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="598c0-102">Comment : enregistrer des messages lorsque l'application démarre ou s'arrête (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="598c0-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="598c0-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="598c0-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="598c0-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` avec les événements `Startup` et `Shutdown` pour enregistrer des informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="598c0-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="598c0-105">Pour accéder au code du gestionnaire d’événements de l’application</span><span class="sxs-lookup"><span data-stu-id="598c0-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="598c0-106">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="598c0-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="598c0-107">Dans le menu **projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="598c0-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="598c0-108">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="598c0-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="598c0-109">Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="598c0-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="598c0-110">Le fichier ApplicationEvents.vb s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="598c0-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="598c0-111">Pour enregistrer des messages quand l’application démarre</span><span class="sxs-lookup"><span data-stu-id="598c0-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="598c0-112">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="598c0-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="598c0-113">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="598c0-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="598c0-114">Dans le menu **Déclarations** , choisissez **Démarrage**.</span><span class="sxs-lookup"><span data-stu-id="598c0-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="598c0-115">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> avant l’exécution de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="598c0-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="598c0-116">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Startup` .</span><span class="sxs-lookup"><span data-stu-id="598c0-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="598c0-117">Pour enregistrer des messages quand l’application s’arrête</span><span class="sxs-lookup"><span data-stu-id="598c0-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="598c0-118">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="598c0-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="598c0-119">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="598c0-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="598c0-120">Dans le menu **Déclarations** , choisissez **Arrêt**.</span><span class="sxs-lookup"><span data-stu-id="598c0-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="598c0-121">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> après l’exécution de l’application principale, mais avant qu’elle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="598c0-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="598c0-122">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Shutdown` .</span><span class="sxs-lookup"><span data-stu-id="598c0-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="598c0-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="598c0-123">Example</span></span>  

 <span data-ttu-id="598c0-124">Vous pouvez utiliser le **Concepteur de projets** pour accéder aux événements de l’application dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="598c0-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="598c0-125">Pour plus d'informations, consultez [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="598c0-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="598c0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="598c0-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="598c0-127">Page Application, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="598c0-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="598c0-128">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="598c0-128">Working with Application Logs</span></span>](working-with-application-logs.md)
