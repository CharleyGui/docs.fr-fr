---
title: Implémentation du modèle asynchrone basé sur des événements
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663706"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c6d02-102">Implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="c6d02-103">Si vous écrivez une classe avec certaines opérations pouvant entraîner d’importants retards, pensez à lui affecter des fonctionnalités asynchrones en implémentant [Vue d’ensemble du modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="c6d02-104">Le modèle asynchrone basé sur des événements fournit une méthode standardisée pour empaqueter une classe incluant des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c6d02-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="c6d02-105">Si elle est implémentée avec des classes d’assistance comme <xref:System.ComponentModel.AsyncOperationManager>, votre classe fonctionnera correctement quel que soit le modèle d’application, notamment ASP.NET, les applications console et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6d02-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="c6d02-106">Pour obtenir un exemple qui implémente le modèle asynchrone basé sur des événements, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="c6d02-107">Le composant <xref:System.ComponentModel.BackgroundWorker> pourra être adapté à des opérations asynchrones simples.</span><span class="sxs-lookup"><span data-stu-id="c6d02-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="c6d02-108">Pour plus d’informations sur <xref:System.ComponentModel.BackgroundWorker>, consultez la page [Guide pratique pour exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="c6d02-109">La liste suivante décrit les fonctionnalités du modèle asynchrone basé sur des événements décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c6d02-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="c6d02-110">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="c6d02-111">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="c6d02-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="c6d02-112">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="c6d02-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="c6d02-113">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="c6d02-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="c6d02-114">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="c6d02-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="c6d02-115">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="c6d02-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="c6d02-116">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="c6d02-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c6d02-117">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="c6d02-118">Envisagez d’implémenter le modèle asynchrone basé sur des événements quand :</span><span class="sxs-lookup"><span data-stu-id="c6d02-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="c6d02-119">Les clients de votre classe n’ont pas besoin que les objets <xref:System.Threading.WaitHandle> et <xref:System.IAsyncResult> soient disponibles pour les opérations asynchrones, ce qui signifie que l’interrogation et <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> devront être développés par le client.</span><span class="sxs-lookup"><span data-stu-id="c6d02-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="c6d02-120">Vous souhaitez que les opérations asynchrones soient gérées par le client avec le modèle d’événement/de délégué familier.</span><span class="sxs-lookup"><span data-stu-id="c6d02-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="c6d02-121">Une opération est un candidat pour une implémentation asynchrone, mais vous devez prendre en compte celles impliquant des latences importantes.</span><span class="sxs-lookup"><span data-stu-id="c6d02-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="c6d02-122">Les opérations tout particulièrement appropriées sont celles dans lesquelles les clients appellent une méthode et sont informés de l’achèvement, sans autre intervention nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c6d02-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="c6d02-123">Sont également appropriées des opérations exécutées en continu et qui informent régulièrement les clients de la progression, des résultats incrémentiels ou des changements d’état.</span><span class="sxs-lookup"><span data-stu-id="c6d02-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="c6d02-124">Pour plus d’informations sur le choix du moment auquel prendre en charge le modèle asynchrone basé sur des événements, consultez [Choix du moment auquel implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="c6d02-125">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="c6d02-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="c6d02-126">Pour chaque méthode synchrone *MethodName* pour laquelle vous souhaitez fournir un équivalent asynchrone :</span><span class="sxs-lookup"><span data-stu-id="c6d02-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="c6d02-127">Décrivez une méthode _MethodName_**Async** qui :</span><span class="sxs-lookup"><span data-stu-id="c6d02-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="c6d02-128">Retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="c6d02-128">Returns `void`.</span></span>

- <span data-ttu-id="c6d02-129">Accepte les mêmes paramètres que la méthode *MethodName*.</span><span class="sxs-lookup"><span data-stu-id="c6d02-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="c6d02-130">Accepte plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="c6d02-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="c6d02-131">Définir en option une surcharge _MethodName_**Async,** identique à _MethodName_**Async** `userState`, mais avec un paramètre supplémentaire de valeur d’objet appelé .</span><span class="sxs-lookup"><span data-stu-id="c6d02-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="c6d02-132">Procédez ainsi si vous êtes prêt à gérer plusieurs appels simultanés de votre méthode, auquel cas la valeur `userState` est remise à tous les gestionnaires d’événements pour distinguer les appels de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c6d02-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="c6d02-133">Vous pouvez également choisir d’en faire un emplacement de stockage de l’état utilisateur pour une récupération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c6d02-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="c6d02-134">Pour chaque signature de méthode _MethodName_**Async** distincte :</span><span class="sxs-lookup"><span data-stu-id="c6d02-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="c6d02-135">Définissez l’événement suivant dans la même classe que la méthode :</span><span class="sxs-lookup"><span data-stu-id="c6d02-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="c6d02-136">Définissez le délégué suivant et <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c6d02-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="c6d02-137">Ils seront probablement définis en dehors de la classe, mais dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c6d02-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - <span data-ttu-id="c6d02-138">Assurez-vous que la classe _MethodName_**CompletedEventArgs** expose ses membres comme des propriétés de lecture seulement, et non des champs, car les champs empêchent la liaison des données.</span><span class="sxs-lookup"><span data-stu-id="c6d02-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="c6d02-139">Ne définissez aucune classe dérivée de <xref:System.ComponentModel.AsyncCompletedEventArgs> pour les méthodes qui ne produisent pas de résultats.</span><span class="sxs-lookup"><span data-stu-id="c6d02-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="c6d02-140">Utilisez simplement une instance de <xref:System.ComponentModel.AsyncCompletedEventArgs> directement.</span><span class="sxs-lookup"><span data-stu-id="c6d02-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="c6d02-141">Il est parfaitement acceptable, lorsque c’est possible et approprié, de réutiliser les types délégué et <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c6d02-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="c6d02-142">Dans ce cas, les appellations ne seront pas aussi cohérentes avec le nom de la méthode, car un délégué donné et <xref:System.ComponentModel.AsyncCompletedEventArgs> ne seront pas liés à une seule méthode.</span><span class="sxs-lookup"><span data-stu-id="c6d02-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="c6d02-143">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="c6d02-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="c6d02-144">Si votre classe prend en charge l’annulation des opérations asynchrones, l’annulation doit être présentée au client comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c6d02-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="c6d02-145">Notez que deux décisions importantes doivent être prises avant de définir l’annulation de la prise en charge :</span><span class="sxs-lookup"><span data-stu-id="c6d02-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="c6d02-146">Votre classe, y compris ses ajouts futurs, comprend-elle une seule opération asynchrone prenant en charge l’annulation ?</span><span class="sxs-lookup"><span data-stu-id="c6d02-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="c6d02-147">Les opérations asynchrones prenant en charge l’annulation de prise en charge peuvent-elles prendre en charge plusieurs opérations en attente ?</span><span class="sxs-lookup"><span data-stu-id="c6d02-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="c6d02-148">Autrement dit, la méthode _MethodName_**Async** prend-elle un `userState` paramètre, et permet-elle de multiples invocations avant d’attendre qu’une fin se termine ?</span><span class="sxs-lookup"><span data-stu-id="c6d02-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="c6d02-149">Utilisez les réponses à ces deux questions dans le tableau ci-dessous pour déterminer la signature de votre méthode d’annulation.</span><span class="sxs-lookup"><span data-stu-id="c6d02-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="c6d02-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6d02-150">Visual Basic</span></span>

||<span data-ttu-id="c6d02-151">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="c6d02-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="c6d02-152">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="c6d02-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="c6d02-153">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="c6d02-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="c6d02-154">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="c6d02-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="c6d02-155">C\#</span><span class="sxs-lookup"><span data-stu-id="c6d02-155">C\#</span></span>

||<span data-ttu-id="c6d02-156">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="c6d02-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="c6d02-157">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="c6d02-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="c6d02-158">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="c6d02-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="c6d02-159">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="c6d02-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="c6d02-160">Si vous définissez la méthode `CancelAsync(object userState)`, les clients doivent être prudents lorsqu’ils choisissent leurs valeurs d’état afin qu’elles soient capables de distinguer toutes les méthodes asynchrones appelées sur l’objet, et pas seulement tous les appels d’une seule méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c6d02-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="c6d02-161">La décision de nommer la version à fonctionnement unique _MethodName_**AsyncCancel** est basée sur la possibilité de découvrir plus facilement la méthode dans un environnement de conception comme IntelliSense de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6d02-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="c6d02-162">Il regroupe les membres associés et les distingue des autres membres qui n’ont rien à voir avec les fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c6d02-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="c6d02-163">Si vous pensez que d’autres opérations asynchrones peuvent être ajoutées dans les versions ultérieures, il est préférable de définir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="c6d02-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="c6d02-164">Ne définissez pas plusieurs méthodes du tableau ci-dessus dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="c6d02-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="c6d02-165">Ceci sera inutile ou risquera d’encombrer l’interface de classe d’un trop grand nombre de méthodes.</span><span class="sxs-lookup"><span data-stu-id="c6d02-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="c6d02-166">Ces méthodes retournent généralement immédiatement et l’opération peut ou non être réellement annulée.</span><span class="sxs-lookup"><span data-stu-id="c6d02-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="c6d02-167">Dans l’événement De l’événement _MethodName_**Completed,** l’objet _MethodName_**CompletedEventArgs** contient un `Cancelled` champ que les clients peuvent utiliser pour déterminer si l’annulation s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c6d02-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="c6d02-168">Respectez la sémantique d’annulation décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="c6d02-169">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="c6d02-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="c6d02-170">Si votre classe ne prend pas en charge plusieurs appels simultanés, envisagez d’exposer une propriété `IsBusy`.</span><span class="sxs-lookup"><span data-stu-id="c6d02-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="c6d02-171">Cela permet aux développeurs de déterminer si une méthode _MethodName_**Async** est en cours d’exécution sans attraper une exception de la méthode _MethodName_**Async.**</span><span class="sxs-lookup"><span data-stu-id="c6d02-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="c6d02-172">Respectez la sémantique `IsBusy` décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="c6d02-173">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="c6d02-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="c6d02-174">Il est généralement souhaitable qu’une opération asynchrone indique sa progression pendant son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="c6d02-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="c6d02-175">Le modèle asynchrone basé sur des événements fournit des instructions pour le faire.</span><span class="sxs-lookup"><span data-stu-id="c6d02-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="c6d02-176">Définissez éventuellement un événement déclenché par l’opération asynchrone et appelé sur le thread approprié.</span><span class="sxs-lookup"><span data-stu-id="c6d02-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="c6d02-177">L’objet <xref:System.ComponentModel.ProgressChangedEventArgs> comporte un indicateur de progression à valeurs entières qui doit être compris entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="c6d02-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="c6d02-178">Nommez cet événement de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="c6d02-178">Name this event as follows:</span></span>

  - <span data-ttu-id="c6d02-179">`ProgressChanged` si la classe comporte plusieurs opérations asynchrones (ou est censée se développer pour inclure plusieurs opérations asynchrones dans les versions ultérieures) ;</span><span class="sxs-lookup"><span data-stu-id="c6d02-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="c6d02-180">_MethodName_**ProgressDm** si la classe a une seule opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c6d02-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="c6d02-181">Ce choix de désignation correspond à celui effectué pour la méthode d’annulation, comme décrit dans la section Annulation facultative de la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c6d02-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="c6d02-182">Cet événement doit utiliser la signature du délégué <xref:System.ComponentModel.ProgressChangedEventHandler> et la classe <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c6d02-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="c6d02-183">En revanche, si un indicateur de progression plus spécifique du domaine peut être fourni (par exemple, les octets lus et nombre total d’octets pour une opération de téléchargement), il est recommandé de définir une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c6d02-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="c6d02-184">Notez qu’il `ProgressChanged` n’y a qu’un seul ou _MethodName_**ProgressChanged** événement pour la classe, quel que soit le nombre de méthodes asynchrones qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="c6d02-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="c6d02-185">On s’attend `userState` à ce que les clients utilisent l’objet qui est transmis aux méthodes _MethodName_**Async** pour distinguer parmi les mises à jour de progression sur les opérations simultanées multiples.</span><span class="sxs-lookup"><span data-stu-id="c6d02-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="c6d02-186">Dans certaines situations, plusieurs opérations prennent en charge la progression et chacune renvoie un indicateur de progression différent.</span><span class="sxs-lookup"><span data-stu-id="c6d02-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="c6d02-187">Dans ce cas, un seul événement `ProgressChanged` n’est pas approprié, et vous pouvez envisager la prise en charge de plusieurs événements `ProgressChanged`.</span><span class="sxs-lookup"><span data-stu-id="c6d02-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="c6d02-188">Dans ce cas, utilisez un modèle de nommage de _MethodName_**ProgressChanged** pour chaque _méthode MethodName_**Async.**</span><span class="sxs-lookup"><span data-stu-id="c6d02-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="c6d02-189">Respectez la sémantique de rapport de progression décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="c6d02-190">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="c6d02-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="c6d02-191">Parfois, une opération asynchrone peut retourner des résultats incrémentiels avant la fin.</span><span class="sxs-lookup"><span data-stu-id="c6d02-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="c6d02-192">Un certain nombre d’options peuvent être utilisées pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="c6d02-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="c6d02-193">En voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="c6d02-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="c6d02-194">Classe à une opération</span><span class="sxs-lookup"><span data-stu-id="c6d02-194">Single-operation Class</span></span>

<span data-ttu-id="c6d02-195">Si votre classe ne prend en charge qu’une seule opération asynchrone et que celle-ci peut retourner des résultats incrémentiels :</span><span class="sxs-lookup"><span data-stu-id="c6d02-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="c6d02-196">Étendre <xref:System.ComponentModel.ProgressChangedEventArgs> le type pour transporter les données de résultat différentiel, et définir un événement**ProgressChanged** _MethodName_avec ces données étendues.</span><span class="sxs-lookup"><span data-stu-id="c6d02-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="c6d02-197">Soulevez cet événement _MethodName_**ProgressChanged** lorsqu’il y a un résultat progressif à signaler.</span><span class="sxs-lookup"><span data-stu-id="c6d02-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="c6d02-198">Cette solution s’applique spécifiquement à une classe d’exploitation unique parce qu’il n’y a aucun problème avec le même événement qui se produit pour retourner les résultats incrémentaux sur «toutes les opérations», comme le fait l’événement**ProgressChanged** _MethodName._</span><span class="sxs-lookup"><span data-stu-id="c6d02-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="c6d02-199">Classe à plusieurs opérations avec des résultats incrémentiels homogènes</span><span class="sxs-lookup"><span data-stu-id="c6d02-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="c6d02-200">Dans ce cas, votre classe prend en charge plusieurs méthodes asynchrones, chacune capable de retourner des résultats incrémentiels, et ces résultats incrémentiels possèdent tous le même type de données.</span><span class="sxs-lookup"><span data-stu-id="c6d02-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="c6d02-201">Suivez le modèle décrit ci-dessus pour les classes à une opération, car la même structure <xref:System.EventArgs> fonctionne pour tous les résultats incrémentiels.</span><span class="sxs-lookup"><span data-stu-id="c6d02-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="c6d02-202">Définissez `ProgressChanged` un événement au lieu d’un événement _MethodName_**ProgressChanged,** puisqu’il s’applique à de multiples méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c6d02-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="c6d02-203">Classe à plusieurs opérations avec des résultats incrémentiels hétérogènes</span><span class="sxs-lookup"><span data-stu-id="c6d02-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="c6d02-204">Si votre classe prend en charge plusieurs méthodes asynchrones, chacune retournant un type de données différent :</span><span class="sxs-lookup"><span data-stu-id="c6d02-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="c6d02-205">Séparez votre rapport de résultat incrémentiel de votre rapport de progression.</span><span class="sxs-lookup"><span data-stu-id="c6d02-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="c6d02-206">Définissez un événement _MethodName_ <xref:System.EventArgs> **ProgressChanged** séparé avec une méthode asynchrone appropriée pour traiter les données de résultat différentiels de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c6d02-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="c6d02-207">Appelez ce gestionnaire d’événements sur le thread approprié comme décrit dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6d02-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="c6d02-208">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="c6d02-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="c6d02-209">Bien que l’utilisation de `out` et `ref` soit en règle générale déconseillée dans le .NET Framework, voici les règles à suivre lorsqu’ils sont présents :</span><span class="sxs-lookup"><span data-stu-id="c6d02-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="c6d02-210">Soit une méthode synchrone *MethodName* :</span><span class="sxs-lookup"><span data-stu-id="c6d02-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="c6d02-211">`out`paramètres de *MethodName* ne doit pas faire partie de _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="c6d02-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="c6d02-212">Au lieu de cela, ils devraient faire partie de _MethodName_**CompletedEventArgs** avec le même nom que son équivalent paramètre dans *MethodName* (sauf s’il ya un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="c6d02-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="c6d02-213">`ref`paramètres de *MethodName* devrait apparaître dans le cadre de _MethodName_**Async**, et dans le cadre de _MethodName_**CompletedEventArgs** avec le même nom que son équivalent paramètre dans *MethodName* (sauf s’il ya un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="c6d02-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="c6d02-214">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c6d02-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="c6d02-215">Votre méthode asynchrone et sa classe <xref:System.ComponentModel.AsyncCompletedEventArgs> se présenteraient ainsi :</span><span class="sxs-lookup"><span data-stu-id="c6d02-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a><span data-ttu-id="c6d02-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6d02-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="c6d02-217">Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="c6d02-218">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="c6d02-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="c6d02-219">Comment : implémenter un formulaire qui utilise une opération d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="c6d02-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="c6d02-220">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="c6d02-221">Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c6d02-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="c6d02-222">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="c6d02-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
