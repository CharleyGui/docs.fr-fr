---
title: Signets-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 7a52823ff68d8f09895bb3a9323a57d3abccd823
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289111"
---
# <a name="bookmarks"></a>Signets

Les signets sont le mécanisme qui permet à une activité d'attendre passivement l'entrée sans maintenir sur un thread de workflow. Lorsqu'une activité signale qu'il attend l'impulsion, il peut créer un signet. Cela indique à l'exécution que l'exécution de l'activité ne doit pas être considérée comme terminé même quand les recettes de méthode (lequel a créé le <xref:System.Activities.Bookmark>) actuellement exécutant.  
  
## <a name="bookmark-basics"></a>Insérer un signet essentiel  

 Un <xref:System.Activities.Bookmark> représente un point auquel l'exécution peut être reprise (et via lequel l'entrée peut être remise) dans une instance de workflow. En général, un nom est attribué à <xref:System.Activities.Bookmark> et le code externe (hôte ou extension) est chargé de reprendre le signet avec les données pertinentes. Lorsqu'un <xref:System.Activities.Bookmark> est continué, l'exécution du workflow planifie le délégué <xref:System.Activities.BookmarkCallback> été associé à ce <xref:System.Activities.Bookmark> au temps de sa création.  
  
## <a name="bookmark-options"></a>Options de signet  

 La classe <xref:System.Activities.BookmarkOptions> spécifie le type de <xref:System.Activities.Bookmark> qui est créé. Les valeurs non mutuellement exclusives possibles sont <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume> et <xref:System.Activities.BookmarkOptions.NonBlocking>. Utilisez <xref:System.Activities.BookmarkOptions.None>, la valeur par défaut, lors de la création d'un <xref:System.Activities.Bookmark> attendu pour être repris une seule fois. Utilisez <xref:System.Activities.BookmarkOptions.MultipleResume> lors de la création d'un <xref:System.Activities.Bookmark> qui peut être repris plusieurs fois. Utilisez <xref:System.Activities.BookmarkOptions.NonBlocking> lors de la création d'un <xref:System.Activities.Bookmark> qui ne peut jamais être continué. Contrairement aux signets créés à l'aide du <xref:System.Activities.BookmarkOptions> par défaut, les signets <xref:System.Activities.BookmarkOptions.NonBlocking> n'empêchent pas une activité d'aboutir.  
  
## <a name="bookmark-resumption"></a>Reprise de signet  

 Les signets peuvent être continués par code en dehors d'un workflow à l'aide de l'une des surcharges <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>. Dans cet exemple, une activité `ReadLine` est créée. Lors de l'exécution, l'activité `ReadLine` crée un <xref:System.Activities.Bookmark>, inscrit un rappel, puis attend la reprise du <xref:System.Activities.Bookmark>. Lors de la reprise, l'activité `ReadLine` affecte les données passées avec le <xref:System.Activities.Bookmark> à son argument <xref:System.Activities.Activity%601.Result%2A>.  
  
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
  
 Dans cet exemple, un workflow qui utilise l'activité `ReadLine` pour rassembler le nom de l'utilisateur et l'afficher dans la fenêtre de console est créé. L'application hôte se charge de rassembler l'ensemble de ces entrées et de les transmettre au workflow en reprenant le <xref:System.Activities.Bookmark>.  
  
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
  
 Lorsque l'activité `ReadLine` est exécutée, elle crée un <xref:System.Activities.Bookmark> nommé `UserName`, puis attend la reprise du signet. L'hôte recueille les données voulues, puis reprend le <xref:System.Activities.Bookmark>. Le workflow reprend, affiche le nom, puis se termine. Notez qu'aucun code de synchronisation n'est obligatoire pour la reprise du signet. Un <xref:System.Activities.Bookmark> peut être continué uniquement lorsque le workflow est inactif, et si le workflow n'est pas inactif, l'appel aux blocs <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> jusqu'à ce que le workflow devienne inactif.  
  
## <a name="bookmark-resumption-result"></a>Résultat de reprise de signet  

 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> retourne une valeur d'énumération <xref:System.Activities.BookmarkResumptionResult> pour indiquer les résultats de la demande de reprise de signet. Les valeurs de retour possibles sont <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady> et <xref:System.Activities.BookmarkResumptionResult.NotFound>. Les hôtes et extensions peuvent utiliser cette valeur pour déterminer comment continuer.
