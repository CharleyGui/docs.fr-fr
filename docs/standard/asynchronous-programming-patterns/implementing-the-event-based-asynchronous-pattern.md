---
title: Implémentation du modèle asynchrone basé sur des événements
description: Découvrez comment implémenter le modèle asynchrone basé sur les événements (EAP) dans .NET. EAP est un moyen standard d’empaqueter une classe qui a des fonctionnalités asynchrones.
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
ms.openlocfilehash: e36ae21e1e03c8c5c688b7446f660ab1bb666a94
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904375"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="0a69d-104">Implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-104">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="0a69d-105">Si vous écrivez une classe avec des opérations qui peuvent entraîner des retards perceptibles, envisagez de lui donner des fonctionnalités asynchrones en implémentant le [modèle asynchrone basé sur les événements](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-105">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern](event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="0a69d-106">Le modèle asynchrone basé sur des événements fournit une méthode standardisée pour empaqueter une classe incluant des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="0a69d-106">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="0a69d-107">Si elle est implémentée avec des classes d’assistance comme <xref:System.ComponentModel.AsyncOperationManager>, votre classe fonctionnera correctement quel que soit le modèle d’application, notamment ASP.NET, les applications console et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0a69d-107">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="0a69d-108">Pour obtenir un exemple qui implémente le modèle asynchrone basé sur des événements, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-108">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="0a69d-109">Le composant <xref:System.ComponentModel.BackgroundWorker> pourra être adapté à des opérations asynchrones simples.</span><span class="sxs-lookup"><span data-stu-id="0a69d-109">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="0a69d-110">Pour plus d’informations sur <xref:System.ComponentModel.BackgroundWorker>, consultez la page [Guide pratique pour exécuter une opération en arrière-plan](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-110">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="0a69d-111">La liste suivante décrit les fonctionnalités du modèle asynchrone basé sur des événements décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0a69d-111">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="0a69d-112">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-112">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="0a69d-113">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="0a69d-113">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="0a69d-114">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="0a69d-114">Optionally Support Cancellation</span></span>

- <span data-ttu-id="0a69d-115">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="0a69d-115">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="0a69d-116">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="0a69d-116">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="0a69d-117">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="0a69d-117">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="0a69d-118">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="0a69d-118">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="0a69d-119">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-119">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="0a69d-120">Envisagez d’implémenter le modèle asynchrone basé sur des événements quand :</span><span class="sxs-lookup"><span data-stu-id="0a69d-120">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="0a69d-121">Les clients de votre classe n’ont pas besoin que les objets <xref:System.Threading.WaitHandle> et <xref:System.IAsyncResult> soient disponibles pour les opérations asynchrones, ce qui signifie que l’interrogation et <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> devront être développés par le client.</span><span class="sxs-lookup"><span data-stu-id="0a69d-121">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="0a69d-122">Vous souhaitez que les opérations asynchrones soient gérées par le client avec le modèle d’événement/de délégué familier.</span><span class="sxs-lookup"><span data-stu-id="0a69d-122">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="0a69d-123">Une opération est un candidat pour une implémentation asynchrone, mais vous devez prendre en compte celles impliquant des latences importantes.</span><span class="sxs-lookup"><span data-stu-id="0a69d-123">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="0a69d-124">Les opérations tout particulièrement appropriées sont celles dans lesquelles les clients appellent une méthode et sont informés de l’achèvement, sans autre intervention nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0a69d-124">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="0a69d-125">Sont également appropriées des opérations exécutées en continu et qui informent régulièrement les clients de la progression, des résultats incrémentiels ou des changements d’état.</span><span class="sxs-lookup"><span data-stu-id="0a69d-125">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="0a69d-126">Pour plus d’informations sur le choix du moment auquel prendre en charge le modèle asynchrone basé sur des événements, consultez [Choix du moment auquel implémenter le modèle asynchrone basé sur des événements](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-126">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="0a69d-127">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="0a69d-127">Naming Asynchronous Methods</span></span>

<span data-ttu-id="0a69d-128">Pour chaque méthode synchrone *MethodName* pour laquelle vous souhaitez fournir un équivalent asynchrone :</span><span class="sxs-lookup"><span data-stu-id="0a69d-128">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="0a69d-129">Définissez une méthode _MethodName_**Async** qui :</span><span class="sxs-lookup"><span data-stu-id="0a69d-129">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="0a69d-130">Retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="0a69d-130">Returns `void`.</span></span>

- <span data-ttu-id="0a69d-131">Accepte les mêmes paramètres que la méthode *MethodName*.</span><span class="sxs-lookup"><span data-stu-id="0a69d-131">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="0a69d-132">Accepte plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="0a69d-132">Accepts multiple invocations.</span></span>

<span data-ttu-id="0a69d-133">Vous pouvez également définir une surcharge _MethodName_**Async** , identique à _MethodName_**Async**, mais avec un paramètre objet supplémentaire appelé `userState` .</span><span class="sxs-lookup"><span data-stu-id="0a69d-133">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="0a69d-134">Procédez ainsi si vous êtes prêt à gérer plusieurs appels simultanés de votre méthode, auquel cas la valeur `userState` est remise à tous les gestionnaires d’événements pour distinguer les appels de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0a69d-134">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="0a69d-135">Vous pouvez également choisir d’en faire un emplacement de stockage de l’état utilisateur pour une récupération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0a69d-135">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="0a69d-136">Pour chaque signature de méthode _MethodName_**Async** distincte :</span><span class="sxs-lookup"><span data-stu-id="0a69d-136">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="0a69d-137">Définissez l’événement suivant dans la même classe que la méthode :</span><span class="sxs-lookup"><span data-stu-id="0a69d-137">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="0a69d-138">Définissez le délégué suivant et <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0a69d-138">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="0a69d-139">Ils seront probablement définis en dehors de la classe, mais dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0a69d-139">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="0a69d-140">Assurez-vous que la classe _MethodName_**CompletedEventArgs** expose ses membres en tant que propriétés en lecture seule et non en tant que champs, car les champs empêchent la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="0a69d-140">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="0a69d-141">Ne définissez aucune classe dérivée de <xref:System.ComponentModel.AsyncCompletedEventArgs> pour les méthodes qui ne produisent pas de résultats.</span><span class="sxs-lookup"><span data-stu-id="0a69d-141">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="0a69d-142">Utilisez simplement une instance de <xref:System.ComponentModel.AsyncCompletedEventArgs> directement.</span><span class="sxs-lookup"><span data-stu-id="0a69d-142">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="0a69d-143">Il est parfaitement acceptable, lorsque c’est possible et approprié, de réutiliser les types délégué et <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0a69d-143">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="0a69d-144">Dans ce cas, les appellations ne seront pas aussi cohérentes avec le nom de la méthode, car un délégué donné et <xref:System.ComponentModel.AsyncCompletedEventArgs> ne seront pas liés à une seule méthode.</span><span class="sxs-lookup"><span data-stu-id="0a69d-144">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="0a69d-145">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="0a69d-145">Optionally Support Cancellation</span></span>

<span data-ttu-id="0a69d-146">Si votre classe prend en charge l’annulation des opérations asynchrones, l’annulation doit être présentée au client comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0a69d-146">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="0a69d-147">Notez que deux décisions importantes doivent être prises avant de définir l’annulation de la prise en charge :</span><span class="sxs-lookup"><span data-stu-id="0a69d-147">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="0a69d-148">Votre classe, y compris ses ajouts futurs, comprend-elle une seule opération asynchrone prenant en charge l’annulation ?</span><span class="sxs-lookup"><span data-stu-id="0a69d-148">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="0a69d-149">Les opérations asynchrones prenant en charge l’annulation de prise en charge peuvent-elles prendre en charge plusieurs opérations en attente ?</span><span class="sxs-lookup"><span data-stu-id="0a69d-149">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="0a69d-150">Autrement dit, la méthode _MethodName_**Async** accepte-t `userState` -elle un paramètre et autorise-t-elle les appels multiples avant d’attendre que l’un d’eux se termine ?</span><span class="sxs-lookup"><span data-stu-id="0a69d-150">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="0a69d-151">Utilisez les réponses à ces deux questions dans le tableau ci-dessous pour déterminer la signature de votre méthode d’annulation.</span><span class="sxs-lookup"><span data-stu-id="0a69d-151">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="0a69d-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a69d-152">Visual Basic</span></span>

||<span data-ttu-id="0a69d-153">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="0a69d-153">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="0a69d-154">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="0a69d-154">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="0a69d-155">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="0a69d-155">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="0a69d-156">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="0a69d-156">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="0a69d-157">C\#</span><span class="sxs-lookup"><span data-stu-id="0a69d-157">C\#</span></span>

||<span data-ttu-id="0a69d-158">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="0a69d-158">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="0a69d-159">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="0a69d-159">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="0a69d-160">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="0a69d-160">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="0a69d-161">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="0a69d-161">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="0a69d-162">Si vous définissez la méthode `CancelAsync(object userState)`, les clients doivent être prudents lorsqu’ils choisissent leurs valeurs d’état afin qu’elles soient capables de distinguer toutes les méthodes asynchrones appelées sur l’objet, et pas seulement tous les appels d’une seule méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="0a69d-162">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="0a69d-163">La décision de nommer _la version d'_ opération asynchrone unique**AsyncCancel** est basée sur la possibilité de découvrir plus facilement la méthode dans un environnement de conception comme IntelliSense de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a69d-163">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="0a69d-164">Il regroupe les membres associés et les distingue des autres membres qui n’ont rien à voir avec les fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="0a69d-164">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="0a69d-165">Si vous pensez que d’autres opérations asynchrones peuvent être ajoutées dans les versions ultérieures, il est préférable de définir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="0a69d-165">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="0a69d-166">Ne définissez pas plusieurs méthodes du tableau ci-dessus dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="0a69d-166">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="0a69d-167">Ceci sera inutile ou risquera d’encombrer l’interface de classe d’un trop grand nombre de méthodes.</span><span class="sxs-lookup"><span data-stu-id="0a69d-167">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="0a69d-168">Ces méthodes retournent généralement immédiatement et l’opération peut ou non être réellement annulée.</span><span class="sxs-lookup"><span data-stu-id="0a69d-168">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="0a69d-169">Dans le gestionnaire d’événements pour l’événement _MethodName_**Completed** , l’objet _MethodName_**CompletedEventArgs** contient un `Cancelled` champ que les clients peuvent utiliser pour déterminer si l’annulation s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0a69d-169">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="0a69d-170">Respectez la sémantique d’annulation décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-170">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="0a69d-171">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="0a69d-171">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="0a69d-172">Si votre classe ne prend pas en charge plusieurs appels simultanés, envisagez d’exposer une propriété `IsBusy`.</span><span class="sxs-lookup"><span data-stu-id="0a69d-172">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="0a69d-173">Cela permet aux développeurs de déterminer si une méthode _MethodName_**Async** s’exécute sans intercepter d’exception de la méthode _MethodName_**Async** .</span><span class="sxs-lookup"><span data-stu-id="0a69d-173">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="0a69d-174">Respectez la sémantique `IsBusy` décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-174">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="0a69d-175">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="0a69d-175">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="0a69d-176">Il est généralement souhaitable qu’une opération asynchrone indique sa progression pendant son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="0a69d-176">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="0a69d-177">Le modèle asynchrone basé sur des événements fournit des instructions pour le faire.</span><span class="sxs-lookup"><span data-stu-id="0a69d-177">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="0a69d-178">Définissez éventuellement un événement déclenché par l’opération asynchrone et appelé sur le thread approprié.</span><span class="sxs-lookup"><span data-stu-id="0a69d-178">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="0a69d-179">L’objet <xref:System.ComponentModel.ProgressChangedEventArgs> comporte un indicateur de progression à valeurs entières qui doit être compris entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="0a69d-179">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="0a69d-180">Nommez cet événement de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="0a69d-180">Name this event as follows:</span></span>

  - <span data-ttu-id="0a69d-181">`ProgressChanged` si la classe comporte plusieurs opérations asynchrones (ou est censée se développer pour inclure plusieurs opérations asynchrones dans les versions ultérieures) ;</span><span class="sxs-lookup"><span data-stu-id="0a69d-181">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="0a69d-182">_MethodName_**ProgressChanged** si la classe a une seule opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="0a69d-182">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="0a69d-183">Ce choix de désignation correspond à celui effectué pour la méthode d’annulation, comme décrit dans la section Annulation facultative de la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="0a69d-183">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="0a69d-184">Cet événement doit utiliser la signature du délégué <xref:System.ComponentModel.ProgressChangedEventHandler> et la classe <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0a69d-184">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="0a69d-185">En revanche, si un indicateur de progression plus spécifique du domaine peut être fourni (par exemple, les octets lus et nombre total d’octets pour une opération de téléchargement), il est recommandé de définir une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0a69d-185">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="0a69d-186">Notez qu’il n’existe qu’un seul `ProgressChanged` événement ou _MethodName_**ProgressChanged** pour la classe, quel que soit le nombre de méthodes asynchrones qu’elle prend en charge.</span><span class="sxs-lookup"><span data-stu-id="0a69d-186">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="0a69d-187">Les clients sont censés utiliser l' `userState` objet passé aux méthodes _MethodName_**Async** pour faire la distinction entre les mises à jour de progression sur plusieurs opérations simultanées.</span><span class="sxs-lookup"><span data-stu-id="0a69d-187">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="0a69d-188">Dans certaines situations, plusieurs opérations prennent en charge la progression et chacune renvoie un indicateur de progression différent.</span><span class="sxs-lookup"><span data-stu-id="0a69d-188">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="0a69d-189">Dans ce cas, un seul événement `ProgressChanged` n’est pas approprié, et vous pouvez envisager la prise en charge de plusieurs événements `ProgressChanged`.</span><span class="sxs-lookup"><span data-stu-id="0a69d-189">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="0a69d-190">Dans ce cas, utilisez un modèle d’affectation de noms de _MethodName_**ProgressChanged** pour chaque méthode _MethodName_**Async** .</span><span class="sxs-lookup"><span data-stu-id="0a69d-190">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="0a69d-191">Respectez la sémantique de rapport de progression décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-191">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="0a69d-192">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="0a69d-192">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="0a69d-193">Parfois, une opération asynchrone peut retourner des résultats incrémentiels avant la fin.</span><span class="sxs-lookup"><span data-stu-id="0a69d-193">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="0a69d-194">Un certain nombre d’options peuvent être utilisées pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="0a69d-194">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="0a69d-195">En voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="0a69d-195">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="0a69d-196">Classe à une opération</span><span class="sxs-lookup"><span data-stu-id="0a69d-196">Single-operation Class</span></span>

<span data-ttu-id="0a69d-197">Si votre classe ne prend en charge qu’une seule opération asynchrone et que celle-ci peut retourner des résultats incrémentiels :</span><span class="sxs-lookup"><span data-stu-id="0a69d-197">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="0a69d-198">Étendez le <xref:System.ComponentModel.ProgressChangedEventArgs> type pour contenir les données de résultat incrémentiel et définissez un événement _MethodName_**ProgressChanged** avec ces données étendues.</span><span class="sxs-lookup"><span data-stu-id="0a69d-198">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="0a69d-199">Déclenche cet événement _MethodName_**ProgressChanged** lorsqu’il existe un résultat incrémentiel à signaler.</span><span class="sxs-lookup"><span data-stu-id="0a69d-199">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="0a69d-200">Cette solution s’applique spécifiquement à une classe d’opération asynchrone unique, car il n’y a aucun problème avec le même événement qui se produit pour retourner des résultats incrémentiels sur « toutes les opérations », comme le fait l’événement _MethodName_**ProgressChanged** .</span><span class="sxs-lookup"><span data-stu-id="0a69d-200">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="0a69d-201">Classe à plusieurs opérations avec des résultats incrémentiels homogènes</span><span class="sxs-lookup"><span data-stu-id="0a69d-201">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="0a69d-202">Dans ce cas, votre classe prend en charge plusieurs méthodes asynchrones, chacune capable de retourner des résultats incrémentiels, et ces résultats incrémentiels possèdent tous le même type de données.</span><span class="sxs-lookup"><span data-stu-id="0a69d-202">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="0a69d-203">Suivez le modèle décrit ci-dessus pour les classes à une opération, car la même structure <xref:System.EventArgs> fonctionne pour tous les résultats incrémentiels.</span><span class="sxs-lookup"><span data-stu-id="0a69d-203">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="0a69d-204">Définissez un `ProgressChanged` événement à la place d’un événement _MethodName_**ProgressChanged** , car il s’applique à plusieurs méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="0a69d-204">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="0a69d-205">Classe à plusieurs opérations avec des résultats incrémentiels hétérogènes</span><span class="sxs-lookup"><span data-stu-id="0a69d-205">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="0a69d-206">Si votre classe prend en charge plusieurs méthodes asynchrones, chacune retournant un type de données différent :</span><span class="sxs-lookup"><span data-stu-id="0a69d-206">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="0a69d-207">Séparez votre rapport de résultat incrémentiel de votre rapport de progression.</span><span class="sxs-lookup"><span data-stu-id="0a69d-207">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="0a69d-208">Définissez un événement _MethodName_**ProgressChanged** distinct avec le approprié <xref:System.EventArgs> pour que chaque méthode asynchrone gère les données de résultat incrémentiel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="0a69d-208">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="0a69d-209">Appelez ce gestionnaire d’événements sur le thread approprié comme décrit dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0a69d-209">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="0a69d-210">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="0a69d-210">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="0a69d-211">Bien que l’utilisation de `out` et `ref` soit en règle générale déconseillée dans le .NET Framework, voici les règles à suivre lorsqu’ils sont présents :</span><span class="sxs-lookup"><span data-stu-id="0a69d-211">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="0a69d-212">Soit une méthode synchrone *MethodName* :</span><span class="sxs-lookup"><span data-stu-id="0a69d-212">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="0a69d-213">`out`les paramètres de *MethodName* ne doivent pas faire partie de _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="0a69d-213">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="0a69d-214">Au lieu de cela, ils doivent faire partie de _MethodName_**CompletedEventArgs** avec le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="0a69d-214">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="0a69d-215">`ref`les paramètres de *MethodName* doivent apparaître dans le cadre de _MethodName_**Async**et dans le cadre de _MethodName_**CompletedEventArgs** portant le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="0a69d-215">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="0a69d-216">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0a69d-216">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="0a69d-217">Votre méthode asynchrone et sa classe <xref:System.ComponentModel.AsyncCompletedEventArgs> se présenteraient ainsi :</span><span class="sxs-lookup"><span data-stu-id="0a69d-217">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a69d-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a69d-218">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="0a69d-219">Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-219">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="0a69d-220">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="0a69d-220">How to: Run an Operation in the Background</span></span>](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="0a69d-221">Comment : implémenter un formulaire qui utilise une opération d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="0a69d-221">How to: Implement a Form That Uses a Background Operation</span></span>](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="0a69d-222">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-222">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="0a69d-223">Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="0a69d-223">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="0a69d-224">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="0a69d-224">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
