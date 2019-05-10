---
title: Classe de base NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 188181211c6171cfce07120b262c2cb798e52ad6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649360"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="d245b-102">Classe de base NativeActivity</span><span class="sxs-lookup"><span data-stu-id="d245b-102">NativeActivity Base Class</span></span>

<span data-ttu-id="d245b-103"><xref:System.Activities.NativeActivity> est une classe abstraite avec un constructeur protégé.</span><span class="sxs-lookup"><span data-stu-id="d245b-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="d245b-104">Comme l'objet <xref:System.Activities.CodeActivity>, la classe <xref:System.Activities.NativeActivity> sert à écrire le comportement impératif en implémentant une méthode <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="d245b-105">Contrairement à l’objet <xref:System.Activities.CodeActivity>, la classe <xref:System.Activities.NativeActivity> a accès à toutes les fonctionnalités exposées de l’exécution du workflow, via l’objet <xref:System.Activities.NativeActivityContext> passé à la méthode <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="d245b-106">Utilisation de NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="d245b-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="d245b-107">Les fonctionnalités de l'exécution du workflow sont accessibles à partir de la méthode <xref:System.Activities.NativeActivity.Execute%2A> en utilisant les membres du paramètre `context`, de type <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="d245b-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="d245b-108">Les fonctionnalités disponibles via <xref:System.Activities.NativeActivityContext> sont notamment :</span><span class="sxs-lookup"><span data-stu-id="d245b-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="d245b-109">obtention et définition d’arguments et de variables ;</span><span class="sxs-lookup"><span data-stu-id="d245b-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="d245b-110">planification d'activités enfants à l'aide de la méthode <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> ;</span><span class="sxs-lookup"><span data-stu-id="d245b-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="d245b-111">abandon de l'exécution de l'activité à l'aide de la méthode <xref:System.Activities.NativeActivityContext.Abort%2A> ;</span><span class="sxs-lookup"><span data-stu-id="d245b-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="d245b-112">annulation de l'exécution de l'enfant à l'aide des méthodes <xref:System.Activities.NativeActivityContext.CancelChild%2A> et <xref:System.Activities.NativeActivityContext.CancelChildren%2A> ;</span><span class="sxs-lookup"><span data-stu-id="d245b-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="d245b-113">accès aux signets d'activité à l'aide de méthodes telles que <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> et <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> ;</span><span class="sxs-lookup"><span data-stu-id="d245b-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="d245b-114">Fonctionnalités de suivi personnalisées à l'aide de <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="d245b-115">accès aux propriétés d'exécution et aux propriétés de valeur de l'activité à l'aide des méthodes <xref:System.Activities.CodeActivityContext.GetProperty%2A> et <xref:System.Activities.NativeActivityContext.GetValue%2A> ;</span><span class="sxs-lookup"><span data-stu-id="d245b-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="d245b-116">planification d'actions et de fonctions de l'activité à l'aide des méthodes <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> et <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="d245b-117">Pour créer une activité personnalisée qui hérite de NativeActivity</span><span class="sxs-lookup"><span data-stu-id="d245b-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="d245b-118">Ouvrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="d245b-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="d245b-119">Sélectionnez **fichier**, **nouveau**, puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="d245b-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="d245b-120">Sélectionnez **Workflow 4.0** sous **Visual C#** dans le **Types de projets** , puis sélectionnez le **v2010** nœud.</span><span class="sxs-lookup"><span data-stu-id="d245b-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="d245b-121">Sélectionnez **bibliothèque d’activités** dans le **modèles** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d245b-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="d245b-122">Nommez le nouveau projet HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="d245b-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="d245b-123">Cliquez sur Activity1.xaml dans le projet HelloActivity et sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d245b-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="d245b-124">Cliquez sur le projet HelloActivity et sélectionnez **ajouter**, puis **classe**.</span><span class="sxs-lookup"><span data-stu-id="d245b-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="d245b-125">Nommez la nouvelle classe HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="d245b-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="d245b-126">Dans le fichier HelloActivity.cs, ajoutez les directives `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="d245b-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="d245b-127">Faites en sorte que la nouvelle classe hérite de <xref:System.Activities.NativeActivity> en ajoutant une classe de base à la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="d245b-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="d245b-128">Ajoutez des fonctionnalités à la classe en ajoutant une méthode <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="d245b-129">Substituez la méthode <xref:System.Activities.NativeActivity.CacheMetadata%2A> et appelez la méthode Add appropriée pour permettre au runtime du workflow de connaître les variables, les arguments, les enfants et les délégués de l'activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d245b-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="d245b-130">Pour plus d'informations, consultez la classe <xref:System.Activities.NativeActivityMetadata>.</span><span class="sxs-lookup"><span data-stu-id="d245b-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="d245b-131">Utilisez l'objet <xref:System.Activities.NativeActivityContext> pour planifier un signet.</span><span class="sxs-lookup"><span data-stu-id="d245b-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="d245b-132">Pour plus d'informations sur la création, la planification et la reprise d'un signet, consultez <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>.</span><span class="sxs-lookup"><span data-stu-id="d245b-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```