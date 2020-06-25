---
title: Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)
description: En savoir plus sur le modèle asynchrone basé sur les tâches (TAP). TAP est le modèle de conception asynchrone recommandé pour le développement dans .NET.
ms.date: 02/26/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 8cef1fcf-6f9f-417c-b21f-3fd8bac75007
ms.openlocfilehash: 21675d26fa2f11d93801e2ba4ffec96b238b97b8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325080"
---
# <a name="task-based-asynchronous-pattern"></a>Modèle asynchrone basé sur les tâches

Le modèle asynchrone basé sur les tâches (TAP) est basé sur <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> les <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> types et de l' <xref:System.Threading.Tasks?displayProperty=nameWithType> espace de noms, qui sont utilisés pour représenter des opérations asynchrones arbitraires. Le TAP est le modèle de conception asynchrone recommandé pour le nouveau développement.  
  
## <a name="naming-parameters-and-return-types"></a>Noms, paramètres et types de retour

Le TAP utilise une méthode unique pour représenter le début et la fin d'une opération asynchrone. Ce fonctionnement le différencie du modèle de programmation asynchrone (APM ou `IAsyncResult`) et du modèle asynchrone basé sur les événements (EAP). Les méthodes `Begin` et `End` sont nécessaires pour le modèle APM. Le modèle EAP a besoin d’une méthode comportant le suffixe `Async`, ainsi que d’un ou plusieurs événements, de types de délégués de gestionnaire d’événements et de types dérivés de `EventArg`. Les méthodes asynchrones du modèle TAP qui retournent des types compatibles await, comme <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> et <xref:System.Threading.Tasks.ValueTask%601>, comprennent le suffixe `Async` après le nom de l’opération. Par exemple, une opération `Get` asynchrone qui retourne une valeur `Task<String>` peut porter le nom `GetAsync`. Si vous ajoutez une méthode TAP à une classe qui contient déjà un nom de méthode EAP avec le suffixe `Async`, utilisez plutôt le suffixe `TaskAsync`. Par exemple, si la classe possède déjà une méthode `GetAsync`, utilisez le nom `GetTaskAsync`. Les méthodes qui lancent une opération asynchrone, mais ne retournent pas de type compatible await, doivent porter un nom qui commence par `Begin`, `Start` ou un autre verbe suggérant qu’elles ne retournent ni ne lèvent le résultat de l’opération.  
  
 Une méthode TAP retourne une <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou une <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, selon que la méthode synchrone correspondante retourne void ou un type `TResult`.  
  
 Les paramètres d’une méthode TAP doivent correspondre à ceux de son équivalent synchrone, dans le même ordre.  Toutefois, les paramètres `out` et `ref` sont exempts de cette règle et doivent être évités entièrement. Les données qui auraient dû être retournées par un paramètre `out` ou `ref` doivent être retournées comme faisant partie du `TResult` retourné par <xref:System.Threading.Tasks.Task%601>, et doivent utiliser un tuple ou une structure de données personnalisée pour s’adapter à plusieurs valeurs. Envisagez également d’ajouter un <xref:System.Threading.CancellationToken> paramètre même si l’équivalent synchrone de la méthode TAP n’en offre pas.

 Les méthodes qui sont consacrées exclusivement à la création, la manipulation ou la combinaison de tâches (où l’intention asynchrone de la méthode est clairement indiquée dans le nom de la méthode ou dans le nom du type auquel la méthode appartient) n’ont pas besoin de suivre ce modèle d’affectation de noms. Ces types de méthodes sont souvent appelés *combinateurs*. Les exemples de combinateurs incluent <xref:System.Threading.Tasks.Task.WhenAll%2A> et <xref:System.Threading.Tasks.Task.WhenAny%2A>, et sont traités dans la section [Utilisation des combinateurs intégrés basés sur des tâches](consuming-the-task-based-asynchronous-pattern.md#combinators) de l'article [Utilisation du modèle asynchrone basé sur les tâches](consuming-the-task-based-asynchronous-pattern.md).  
  
 Pour obtenir des exemples de la façon dont la syntaxe du TAP diffère de celle utilisée dans les modèles de programmation asynchrones hérités tels que le modèle de programmation asynchrone (APM) et le modèle asynchrone basé sur des événements (EAP), consultez [Modèles de programmation asynchrone](index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Lancer une opération asynchrone  
 Une méthode asynchrone basée sur le TAP peut effectuer une petite quantité de travail de façon synchrone, comme valider les arguments et initialiser l’opération asynchrone, avant de retourner la tâche résultante. Le travail synchrone doit être conservé au minimum afin que la méthode asynchrone puisse retourner rapidement. Les raisons d’un retour rapide sont les suivantes :  
  
- Les méthodes asynchrones peuvent être appelées par des threads d'interface utilisateur, et tout travail synchrone de longue durée peut nuire à la réactivité de l'application.  
  
- Plusieurs méthodes asynchrones peuvent être lancées simultanément. Par conséquent, tout travail de longue durée dans la partie synchrone d'une méthode asynchrone risque de retarder l'initiation d'autres opérations asynchrones, réduisant ainsi les avantages offerts par l'accès concurrentiel.  
  
 Dans certains cas, la quantité de travail nécessaire pour terminer l'opération est inférieure à la quantité de travail nécessaire pour lancer l'opération de façon asynchrone. La lecture d'un flux où l'opération de lecture peut être satisfaite par les données déjà mises en mémoire tampon est un exemple de ce type de scénario. Dans de tels cas, l'opération peut s'exécuter de façon synchrone et peut retourner une tâche qui a déjà été effectuée.  
  
## <a name="exceptions"></a>Exceptions  
 Une méthode asynchrone doit lever une exception pour être rejetée de l'appel de méthode asynchrone uniquement en réponse à une erreur d'utilisation. Les erreurs d'utilisation ne doivent jamais se produire dans le code de production. Par exemple, si le passage d’une référence null ( `Nothing` dans Visual Basic) comme arguments de la méthode provoque un état d’erreur (généralement représenté par une <xref:System.ArgumentNullException> exception), vous pouvez modifier le code appelant pour vous assurer qu’une référence null n’est jamais passée. Pour toutes les autres erreurs, les exceptions qui se produisent lorsqu'une méthode asynchrone est en cours d'exécution doivent être assignées à la tâche retournée, même si la méthode asynchrone se termine avant que la tâche ne soit retournée. En général, une tâche contient au plus une exception. Toutefois, si la tâche représente plusieurs opérations (par exemple, <xref:System.Threading.Tasks.Task.WhenAll%2A>), plusieurs exceptions peuvent être associées à une tâche unique.  
  
## <a name="target-environment"></a>Environnement cible  
 Lorsque vous implémentez une méthode TAP, il est possible de déterminer où l'exécution asynchrone se produit. Vous pouvez choisir d’exécuter la charge de travail sur le pool de threads, de l’implémenter à l’aide d’e/s asynchrones (sans être lié à un thread pour la majorité de l’exécution de l’opération), de l’exécuter sur un thread spécifique (tel que le thread d’interface utilisateur) ou d’utiliser un nombre quelconque de contextes potentiels. Une méthode TAP peut même ne rien avoir à exécuter et simplement retourner une <xref:System.Threading.Tasks.Task> qui représente l’occurrence d’une condition ailleurs dans le système (par exemple, une tâche qui représente des données reçues par une structure de données en file d’attente).

 L’appelant de la méthode TAP peut bloquer l’attente de l’exécution de la méthode TAP par une attente synchrone sur la tâche obtenue, ou il peut exécuter du code supplémentaire (continuation) quand l’opération asynchrone est terminée. Le créateur du code de continuation a le contrôle sur l'endroit où ce code s'exécute. Il est possible de créer le code de continuation explicitement, via des méthodes sur la classe <xref:System.Threading.Tasks.Task> (par exemple, <xref:System.Threading.Tasks.Task.ContinueWith%2A>) ou implicitement, à l'aide de la prise en charge des langages par les continuations (par exemple, `await` en C#, `Await` en Visual Basic, `AwaitValue` en F#).  
  
## <a name="task-status"></a>État des tâches  
 La classe <xref:System.Threading.Tasks.Task> fournit un cycle de vie pour les opérations asynchrones, et ce cycle est représenté par l'énumération <xref:System.Threading.Tasks.TaskStatus>. Pour prendre en charge les cas extrêmes de types qui dérivent de <xref:System.Threading.Tasks.Task> et de <xref:System.Threading.Tasks.Task%601>, et pour prendre en charge la séparation de la construction et de la planification, la classe <xref:System.Threading.Tasks.Task> expose une méthode <xref:System.Threading.Tasks.Task.Start%2A>. Les tâches créées par les constructeurs <xref:System.Threading.Tasks.Task> publics sont connues sous le nom de *tâches passives*, car elles démarrent leur cycle de vie dans l'état <xref:System.Threading.Tasks.TaskStatus.Created> non planifié et sont planifiées uniquement quand la méthode <xref:System.Threading.Tasks.Task.Start%2A> est appelée sur ces instances.

 Toutes les autres tâches démarrent leur cycle de vie dans un état réactif, ce qui signifie que les opérations asynchrones qu’elles représentent ont déjà été initialisées et que leur état de tâche est une valeur d’énumération autre que <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Toutes les tâches qui sont retournées par les méthodes TAP doivent être activées. **Si une méthode TAP utilise en interne le constructeur d’une tâche pour instancier la tâche à retourner, la méthode TAP doit appeler <xref:System.Threading.Tasks.Task.Start%2A> sur l' <xref:System.Threading.Tasks.Task> objet avant de la retourner.** Les consommateurs d’une méthode TAP peuvent sans risque supposer que la tâche retournée est active et ne doivent pas essayer d’appeler la méthode <xref:System.Threading.Tasks.Task.Start%2A> sur une <xref:System.Threading.Tasks.Task> qui est retournée à partir d’une méthode TAP. L'appel de la méthode <xref:System.Threading.Tasks.Task.Start%2A> sur une tâche active entraîne la levée d'une exception <xref:System.InvalidOperationException>.  
  
## <a name="cancellation-optional"></a>Annulation (facultatif)  
 Dans le TAP, l'annulation est facultative pour les implémenteurs de méthodes asynchrones et les consommateurs de méthodes asynchrones. Si une opération autorise l'annulation, elle expose une surcharge de la méthode asynchrone qui accepte un jeton d'annulation (instance de <xref:System.Threading.CancellationToken>). Par convention, le paramètre est nommé `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 L'opération asynchrone surveille ce jeton en cas de demandes d'annulation. Si elle reçoit une demande d'annulation, elle peut choisir d'honorer cette demande et d'annuler l'opération. Si la demande d’annulation provoque l’arrêt prématuré du travail, la méthode TAP retourne une tâche qui se termine dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled> ; il n’existe aucun résultat disponible et aucune exception n’est levée.  L’état <xref:System.Threading.Tasks.TaskStatus.Canceled> est considéré comme un état final (terminé) pour une tâche, il en est de même pour les états <xref:System.Threading.Tasks.TaskStatus.Faulted> et <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>. Par conséquent, si une tâche est dans l'état <xref:System.Threading.Tasks.TaskStatus.Canceled>, sa propriété <xref:System.Threading.Tasks.Task.IsCompleted%2A> retourne la valeur `true`. Lorsqu'une tâche se termine dans l'état <xref:System.Threading.Tasks.TaskStatus.Canceled>, toutes les continuations enregistrées avec la tâche sont planifiées ou exécutées, sauf si une option de continuation telle que <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> a été spécifiée pour quitter la continuation. Tout code qui attend de façon asynchrone une tâche annulée via l'utilisation de fonctionnalités de langage continue de s'exécuter mais reçoit une exception <xref:System.OperationCanceledException> ou une exception qui en dérive. Le code qui est bloqué de manière synchrone en attendant la tâche via des méthodes telles que <xref:System.Threading.Tasks.Task.Wait%2A> et <xref:System.Threading.Tasks.Task.WaitAll%2A> continue également de s’exécuter avec une exception.  
  
 Si un jeton d’annulation a demandé l’annulation avant que la méthode TAP qui accepte le jeton ne soit appelée, la méthode TAP doit retourner une tâche <xref:System.Threading.Tasks.TaskStatus.Canceled>.  Toutefois, si l'annulation est demandée alors que l'opération asynchrone est en cours d'exécution, l'opération asynchrone n'a pas besoin d'accepter la demande d'annulation.  La tâche retournée doit se terminer dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled> uniquement si l’opération se termine à la suite de la demande d’annulation. Si l'annulation est demandée mais qu'un résultat (ou une exception) est tout de même produit, la tâche doit se terminer dans l'état <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> ou <xref:System.Threading.Tasks.TaskStatus.Faulted>.

 Pour les méthodes asynchrones qui souhaitent exposer la possibilité d’être annulées en premier et en avant, vous n’avez pas besoin de fournir une surcharge qui n’accepte pas de jeton d’annulation. Pour les méthodes qui ne peuvent pas être annulées, ne fournissez aucune surcharge acceptant un jeton d'annulation ; cela permet d'indiquer à l'appelant si la méthode cible est réellement annulable ou non.  Le code de consommateur qui ne souhaite pas l’annulation peut appeler une méthode qui accepte un <xref:System.Threading.CancellationToken> et fournit <xref:System.Threading.CancellationToken.None%2A> comme valeur d’argument. <xref:System.Threading.CancellationToken.None%2A> est fonctionnellement équivalent au <xref:System.Threading.CancellationToken> par défaut.  
  
## <a name="progress-reporting-optional"></a>Rapport de progression (facultatif)  
 Certaines opérations asynchrones tirent parti de la fourniture de notifications de progression ; elles sont généralement utilisées pour mettre à jour une interface utilisateur avec des informations sur la progression de l'opération asynchrone.

 Dans le TAP, la progression est gérée via une interface <xref:System.IProgress%601>, qui est passée à la méthode asynchrone en tant que paramètre généralement nommé `progress`.  Le fait de fournir l'interface de progression lorsque la méthode asynchrone est appelée aide à éliminer les conditions de concurrence qui résultent d'une utilisation incorrecte (autrement dit, lorsque les gestionnaires d'événements enregistrés de façon incorrecte après le démarrage de l'opération sont susceptibles de manquer des mises à jour).  Plus important encore, l'interface de progression prend en charge diverses implémentations de progression, comme indiqué par le code de consommation.  Par exemple, le code de consommation peut uniquement s’intéresser à la dernière mise à jour de la progression, ou peut vouloir mettre en mémoire tampon toutes les mises à jour, ou peut vouloir appeler une action pour chaque mise à jour, ou peut vouloir vérifier si l’appel est marshalé à un thread particulier. Toutes ces options peuvent être obtenues à l’aide d’une implémentation différente de l’interface, personnalisée en fonction des besoins particuliers du consommateur.  Comme pour l'annulation, les implémentations du TAP doivent fournir un paramètre <xref:System.IProgress%601> uniquement si l'API prend en charge les notifications de progression.

 Par exemple, si la méthode `ReadAsync` décrite précédemment dans cet article peut indiquer la progression intermédiaire sous la forme du nombre d'octets lus jusqu'ici, le rappel de progression peut être une interface <xref:System.IProgress%601> :  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Si une `FindFilesAsync` méthode retourne une liste de tous les fichiers qui correspondent à un modèle de recherche particulier, le rappel de progression peut fournir une estimation du pourcentage de travail effectué et de l’ensemble actuel des résultats partiels. Il peut fournir ces informations avec un tuple :  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ou avec un type de données spécifique à l’API :  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 Dans le second cas, le type de données particulier possède généralement le suffixe `ProgressInfo`.  
  
 Si les implémentations du TAP fournissent des surcharges qui acceptent un `progress` paramètre, elles doivent permettre à l’argument d’être `null` , auquel cas aucune progression n’est signalée. Les implémentations de TAP doivent signaler la progression de l' <xref:System.Progress%601> objet de façon synchrone, ce qui permet à la méthode asynchrone de fournir rapidement la progression. Elle permet également au consommateur de la progression de déterminer comment et où il est préférable de gérer les informations. Par exemple, l'instance de progression peut choisir de marshaler les rappels et de déclencher des événements dans un contexte de synchronisation capturé.  
  
## <a name="iprogresst-implementations"></a>\<T>Implémentations de IProgress  
 .NET Framework 4.5 fournit une implémentation unique de <xref:System.IProgress%601> : <xref:System.Progress%601>. La classe <xref:System.Progress%601> est déclarée comme suit :  
  
```csharp  
public class Progress<T> : IProgress<T>  
{  
    public Progress();  
    public Progress(Action<T> handler);  
    protected virtual void OnReport(T value);  
    public event EventHandler<T> ProgressChanged;  
}  
```  
  
```vb  
Public Class Progress(Of T) : Inherits IProgress(Of T)  
    Public Sub New()  
    Public Sub New(handler As Action(Of T))  
    Protected Overridable Sub OnReport(value As T)  
    Public Event ProgressChanged As EventHandler(Of T>  
End Class  
```  
  
 Une instance de <xref:System.Progress%601> expose un événement <xref:System.Progress%601.ProgressChanged>, qui est déclenché chaque fois que l'opération asynchrone signale une mise à jour de la progression. L'événement <xref:System.Progress%601.ProgressChanged> est déclenché sur l'objet <xref:System.Threading.SynchronizationContext> qui a été capturé lorsque l'instance de <xref:System.Progress%601> a été instanciée. Si aucun contexte de synchronisation n’est disponible, un contexte par défaut qui cible le pool de threads est utilisé. Les gestionnaires peuvent être enregistrés avec cet événement. Un gestionnaire unique peut également être fourni au constructeur <xref:System.Progress%601> pour des raisons pratiques, et se comporter comme un gestionnaire d'événements pour l'événement <xref:System.Progress%601.ProgressChanged>. Les mises à jour de progression sont déclenchées de façon asynchrone afin d'éviter de différer l'opération asynchrone alors que les gestionnaires d'événements s'exécutent. Une autre implémentation de <xref:System.IProgress%601> peut choisir d'appliquer une sémantique différente.  
  
## <a name="choosing-the-overloads-to-provide"></a>Choisir les surcharges à fournir  
 Si une implémentation du TAP utilise des paramètres facultatifs <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> et <xref:System.IProgress%601>, elle est susceptible de nécessiter jusqu'à quatre surcharges :  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
public Task MethodNameAsync(…, IProgress<T> progress);
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken cancellationToken) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Toutefois, de nombreuses implémentations de TAP ne fournissent pas de fonctionnalités d’annulation ou de progression, donc elles nécessitent une seule méthode :  
  
```csharp  
public Task MethodNameAsync(…);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
```  
  
 Si une implémentation du TAP prend en charge l'annulation ou la progression, mais pas les deux, elle peut fournir deux surcharges :  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
  
// … or …  
  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken) As Task  
  
' … or …  
  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task  
```  
  
 Si une implémentation du TAP prend en charge l'annulation et la progression, elle peut exposer les quatre surcharges. Toutefois, elle peut fournir uniquement les deux suivantes :  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Pour compenser les deux combinaisons intermédiaires manquantes, les développeurs peuvent passer <xref:System.Threading.CancellationToken.None%2A> ou un <xref:System.Threading.CancellationToken> par défaut pour le paramètre `cancellationToken` et la valeur `null` pour le paramètre `progress`.  
  
 Si vous vous attendez à ce que chaque utilisation de la méthode TAP prenne en charge l’annulation ou la progression, vous pouvez omettre les surcharges qui n’acceptent pas le paramètre approprié.  
  
 Si vous décidez d’exposer plusieurs surcharges pour rendre l’annulation ou la progression facultative, les surcharges qui ne prennent pas en charge l’annulation ou la progression doivent se comporter comme si elles étaient passées <xref:System.Threading.CancellationToken.None%2A> pour l’annulation ou `null` pour progresser vers la surcharge qui les prend en charge.  
  
## <a name="related-articles"></a>Articles connexes
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Modèles de programmation asynchrone](index.md)|Présente les trois modèles permettant d'effectuer des opérations asynchrones : le modèle asynchrone basé sur des tâches (TAP), le modèle de programmation asynchrone (APM) et le modèle asynchrone basé sur des événements (EAP).|  
|[Implémentation du modèle asynchrone basé sur des tâches](implementing-the-task-based-asynchronous-pattern.md)|Décrit comment implémenter le modèle asynchrone basé sur des tâches (TAP) de trois façons : à l'aide des compilateurs C# et Visual Basic dans Visual Studio, manuellement, ou par une combinaison des méthodes du compilateur et des méthodes manuelles.|  
|[Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md)|Décrit comment utiliser des tâches et des rappels afin de terminer l’attente sans blocage.|  
|[Interopérabilité avec d’autres types et modèles asynchrones](interop-with-other-asynchronous-patterns-and-types.md)|Décrit comment utiliser le modèle asynchrone basé sur des tâches (TAP) pour implémenter le modèle de programmation asynchrone (APM) et le modèle asynchrone basé sur des événements (EAP).|
