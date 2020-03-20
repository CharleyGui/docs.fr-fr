---
title: Signets - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183012"
---
# <a name="bookmarks"></a><span data-ttu-id="72828-102">Signets</span><span class="sxs-lookup"><span data-stu-id="72828-102">Bookmarks</span></span>
<span data-ttu-id="72828-103">Les signets sont le mécanisme qui permet à une activité d'attendre passivement l'entrée sans maintenir sur un thread de workflow.</span><span class="sxs-lookup"><span data-stu-id="72828-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="72828-104">Lorsqu'une activité signale qu'il attend l'impulsion, il peut créer un signet.</span><span class="sxs-lookup"><span data-stu-id="72828-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="72828-105">Cela indique à l'exécution que l'exécution de l'activité ne doit pas être considérée comme terminé même quand les recettes de méthode (lequel a créé le <xref:System.Activities.Bookmark>) actuellement exécutant.</span><span class="sxs-lookup"><span data-stu-id="72828-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="72828-106">Insérer un signet essentiel</span><span class="sxs-lookup"><span data-stu-id="72828-106">Bookmark Basics</span></span>  
 <span data-ttu-id="72828-107">Un <xref:System.Activities.Bookmark> représente un point auquel l'exécution peut être reprise (et via lequel l'entrée peut être remise) dans une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="72828-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="72828-108">En général, un nom est attribué à <xref:System.Activities.Bookmark> et le code externe (hôte ou extension) est chargé de reprendre le signet avec les données pertinentes.</span><span class="sxs-lookup"><span data-stu-id="72828-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="72828-109">Lorsqu'un <xref:System.Activities.Bookmark> est continué, l'exécution du workflow planifie le délégué <xref:System.Activities.BookmarkCallback> été associé à ce <xref:System.Activities.Bookmark> au temps de sa création.</span><span class="sxs-lookup"><span data-stu-id="72828-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="72828-110">Options de signet</span><span class="sxs-lookup"><span data-stu-id="72828-110">Bookmark Options</span></span>  
 <span data-ttu-id="72828-111">La classe <xref:System.Activities.BookmarkOptions> spécifie le type de <xref:System.Activities.Bookmark> qui est créé.</span><span class="sxs-lookup"><span data-stu-id="72828-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="72828-112">Les valeurs non mutuellement exclusives possibles sont <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume> et <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="72828-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="72828-113">Utilisez <xref:System.Activities.BookmarkOptions.None>, la valeur par défaut, lors de la création d'un <xref:System.Activities.Bookmark> attendu pour être repris une seule fois.</span><span class="sxs-lookup"><span data-stu-id="72828-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="72828-114">Utilisez <xref:System.Activities.BookmarkOptions.MultipleResume> lors de la création d'un <xref:System.Activities.Bookmark> qui peut être repris plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="72828-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="72828-115">Utilisez <xref:System.Activities.BookmarkOptions.NonBlocking> lors de la création d'un <xref:System.Activities.Bookmark> qui ne peut jamais être continué.</span><span class="sxs-lookup"><span data-stu-id="72828-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="72828-116">Contrairement aux signets créés à l'aide du <xref:System.Activities.BookmarkOptions> par défaut, les signets <xref:System.Activities.BookmarkOptions.NonBlocking> n'empêchent pas une activité d'aboutir.</span><span class="sxs-lookup"><span data-stu-id="72828-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="72828-117">Reprise de signet</span><span class="sxs-lookup"><span data-stu-id="72828-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="72828-118">Les signets peuvent être continués par code en dehors d'un workflow à l'aide de l'une des surcharges <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="72828-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="72828-119">Dans cet exemple, une activité `ReadLine` est créée.</span><span class="sxs-lookup"><span data-stu-id="72828-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="72828-120">Lors de l'exécution, l'activité `ReadLine` crée un <xref:System.Activities.Bookmark>, inscrit un rappel, puis attend la reprise du <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="72828-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="72828-121">Lors de la reprise, l'activité `ReadLine` affecte les données passées avec le <xref:System.Activities.Bookmark> à son argument <xref:System.Activities.Activity%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="72828-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="72828-122">Dans cet exemple, un workflow qui utilise l'activité `ReadLine` pour rassembler le nom de l'utilisateur et l'afficher dans la fenêtre de console est créé.</span><span class="sxs-lookup"><span data-stu-id="72828-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="72828-123">L'application hôte se charge de rassembler l'ensemble de ces entrées et de les transmettre au workflow en reprenant le <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="72828-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="72828-124">Lorsque l'activité `ReadLine` est exécutée, elle crée un <xref:System.Activities.Bookmark> nommé `UserName`, puis attend la reprise du signet.</span><span class="sxs-lookup"><span data-stu-id="72828-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="72828-125">L'hôte recueille les données voulues, puis reprend le <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="72828-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="72828-126">Le workflow reprend, affiche le nom, puis se termine.</span><span class="sxs-lookup"><span data-stu-id="72828-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="72828-127">Notez qu'aucun code de synchronisation n'est obligatoire pour la reprise du signet.</span><span class="sxs-lookup"><span data-stu-id="72828-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="72828-128">Un <xref:System.Activities.Bookmark> peut être continué uniquement lorsque le workflow est inactif, et si le workflow n'est pas inactif, l'appel aux blocs <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> jusqu'à ce que le workflow devienne inactif.</span><span class="sxs-lookup"><span data-stu-id="72828-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="72828-129">Résultat de reprise de signet</span><span class="sxs-lookup"><span data-stu-id="72828-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="72828-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> retourne une valeur d'énumération <xref:System.Activities.BookmarkResumptionResult> pour indiquer les résultats de la demande de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="72828-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="72828-131">Les valeurs de retour possibles sont <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady> et <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="72828-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="72828-132">Les hôtes et extensions peuvent utiliser cette valeur pour déterminer comment continuer.</span><span class="sxs-lookup"><span data-stu-id="72828-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
