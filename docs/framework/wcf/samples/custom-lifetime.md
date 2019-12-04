---
title: Durée de vie personnalisée
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715479"
---
# <a name="custom-lifetime"></a><span data-ttu-id="969e9-102">Durée de vie personnalisée</span><span class="sxs-lookup"><span data-stu-id="969e9-102">Custom lifetime</span></span>

<span data-ttu-id="969e9-103">Cet exemple montre comment écrire une extension Windows Communication Foundation (WCF) pour fournir des services de durée de vie personnalisés pour les instances de service WCF partagées.</span><span class="sxs-lookup"><span data-stu-id="969e9-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="969e9-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="969e9-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="969e9-105">Instanciation partagée</span><span class="sxs-lookup"><span data-stu-id="969e9-105">Shared instancing</span></span>

<span data-ttu-id="969e9-106">WCF offre plusieurs modes d’instanciation pour vos instances de service.</span><span class="sxs-lookup"><span data-stu-id="969e9-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="969e9-107">Le mode d’instanciation partagé abordé dans cet article fournit un moyen de partager une instance de service entre plusieurs canaux.</span><span class="sxs-lookup"><span data-stu-id="969e9-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="969e9-108">Les clients peuvent contacter une méthode de fabrique dans le service et créer un nouveau canal pour démarrer la communication.</span><span class="sxs-lookup"><span data-stu-id="969e9-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="969e9-109">L’extrait de code suivant montre comment une application cliente crée un canal vers une instance de service existante :</span><span class="sxs-lookup"><span data-stu-id="969e9-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="969e9-110">Contrairement aux autres modes d'instanciation, l'instanciation partagée a une façon unique de libérer des instances de service.</span><span class="sxs-lookup"><span data-stu-id="969e9-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="969e9-111">Par défaut, lorsque tous les canaux sont fermés pour une <xref:System.ServiceModel.InstanceContext>, le runtime du service WCF vérifie si le service <xref:System.ServiceModel.InstanceContextMode> est configuré pour <xref:System.ServiceModel.InstanceContextMode.PerCall> ou <xref:System.ServiceModel.InstanceContextMode.PerSession>, et si c’est le cas, libère l’instance et réclame les ressources.</span><span class="sxs-lookup"><span data-stu-id="969e9-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="969e9-112">Si un <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> personnalisé est utilisé, WCF appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de l’implémentation du fournisseur avant de libérer l’instance.</span><span class="sxs-lookup"><span data-stu-id="969e9-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="969e9-113">Si <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> retourne `true` l’instance est libérée, dans le cas contraire, l’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est chargée de notifier la `Dispatcher` de l’état inactif à l’aide d’une méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="969e9-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="969e9-114">Pour ce faire, appelez la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="969e9-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="969e9-115">Cet exemple montre comment vous pouvez différer la libération du <xref:System.ServiceModel.InstanceContext> avec un délai d’inactivité de 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="969e9-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="969e9-116">Extension de l'InstanceContext</span><span class="sxs-lookup"><span data-stu-id="969e9-116">Extending the InstanceContext</span></span>

<span data-ttu-id="969e9-117">Dans WCF, <xref:System.ServiceModel.InstanceContext> est le lien entre l’instance de service et le `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="969e9-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="969e9-118">WCF vous permet d’étendre ce composant d’exécution en ajoutant un nouvel État ou comportement à l’aide de son modèle d’objet extensible.</span><span class="sxs-lookup"><span data-stu-id="969e9-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="969e9-119">Le modèle d’objet extensible est utilisé dans WCF pour étendre des classes d’exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d’État à un objet.</span><span class="sxs-lookup"><span data-stu-id="969e9-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="969e9-120">Le modèle d'objet extensible contient trois interfaces : <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601> et <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="969e9-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="969e9-121">L’interface <xref:System.ServiceModel.IExtensibleObject%601> est implémentée par des objets pour autoriser des extensions qui personnalisent leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="969e9-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="969e9-122">L’interface <xref:System.ServiceModel.IExtension%601> est implémentée par des objets qui peuvent être des extensions de classes de type `T`.</span><span class="sxs-lookup"><span data-stu-id="969e9-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="969e9-123">Enfin, l’interface <xref:System.ServiceModel.IExtensionCollection%601> est une collection d’implémentations de <xref:System.ServiceModel.IExtension%601> qui permet de récupérer une implémentation de <xref:System.ServiceModel.IExtension%601> par leur type.</span><span class="sxs-lookup"><span data-stu-id="969e9-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="969e9-124">Par conséquent, pour étendre le <xref:System.ServiceModel.InstanceContext>, vous devez implémenter l’interface <xref:System.ServiceModel.IExtension%601>.</span><span class="sxs-lookup"><span data-stu-id="969e9-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="969e9-125">Dans cet exemple de projet, la classe `CustomLeaseExtension` contient cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="969e9-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="969e9-126">L'interface <xref:System.ServiceModel.IExtension%601> possède deux méthodes : <xref:System.ServiceModel.IExtension%601.Attach%2A> et <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="969e9-127">Comme leur nom le laisse supposer, ces deux méthodes sont appelées lorsque le runtime attache l’extension à une instance de la classe <xref:System.ServiceModel.InstanceContext> et l’en détache.</span><span class="sxs-lookup"><span data-stu-id="969e9-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="969e9-128">Dans cet exemple, la méthode `Attach` est utilisée pour effectuer le suivi de l’objet <xref:System.ServiceModel.InstanceContext> qui appartient à l’instance actuelle de l’extension.</span><span class="sxs-lookup"><span data-stu-id="969e9-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="969e9-129">En outre, vous devez ajouter l’implémentation dont l’extension a besoin pour fournir la prise en charge de la durée de vie étendue.</span><span class="sxs-lookup"><span data-stu-id="969e9-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="969e9-130">Par conséquent, l’interface `ICustomLease` est déclarée avec les méthodes souhaitées et est implémentée dans la classe `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="969e9-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="969e9-131">Lorsque WCF appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> dans l’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, cet appel est routé vers la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de l' `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="969e9-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="969e9-132">Ensuite, le `CustomLeaseExtension` vérifie son état privé pour déterminer si le <xref:System.ServiceModel.InstanceContext> est inactif.</span><span class="sxs-lookup"><span data-stu-id="969e9-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="969e9-133">S’il est inactif, il retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="969e9-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="969e9-134">Sinon, elle démarre un minuteur pour l'extension spécifiée de la durée de vie.</span><span class="sxs-lookup"><span data-stu-id="969e9-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="969e9-135">Dans l’événement `Elapsed` de la minuterie, la fonction de rappel dans le répartiteur est appelée afin de démarrer un autre cycle de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="969e9-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="969e9-136">Il n’existe aucun moyen de renouveler le minuteur en cours d’exécution lorsqu’un nouveau message arrive pour l’instance déplacée vers l’état inactif.</span><span class="sxs-lookup"><span data-stu-id="969e9-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="969e9-137">L'exemple implémente <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> pour intercepter les appels à la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> et les router vers `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="969e9-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="969e9-138">L'implémentation d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est contenue dans la classe `CustomLifetimeLease`.</span><span class="sxs-lookup"><span data-stu-id="969e9-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="969e9-139">La méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> est appelée lorsque WCF est sur le paragraphe de libérer l’instance de service.</span><span class="sxs-lookup"><span data-stu-id="969e9-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="969e9-140">Toutefois, il n'existe qu'une instance d'une implémentation d'`ISharedSessionInstance` particulière dans la collection <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> du ServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="969e9-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="969e9-141">Cela signifie qu’il n’existe aucun moyen de savoir si la <xref:System.ServiceModel.InstanceContext> est fermée au moment où WCF vérifie la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="969e9-142">Par conséquent, cet exemple utilise le verrouillage de thread pour sérialiser les requêtes vers la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="969e9-143">Le recours au verrouillage de threads n'est pas une approche recommandée, car la sérialisation peut considérablement affecter les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="969e9-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="969e9-144">Un champ de membre privé est utilisé dans la classe `CustomLifetimeLease` pour suivre l’état inactif et est retourné par la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="969e9-145">Chaque fois que la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> est appelée, le champ `isIdle` est retourné et réinitialisé à `false`.</span><span class="sxs-lookup"><span data-stu-id="969e9-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="969e9-146">L'affectation de `false` à cette valeur est indispensable pour que le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="969e9-147">Si la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> retourne `false`, le répartiteur inscrit une fonction de rappel à l’aide de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="969e9-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="969e9-148">Cette méthode reçoit une référence à l’<xref:System.ServiceModel.InstanceContext> libéré.</span><span class="sxs-lookup"><span data-stu-id="969e9-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="969e9-149">Par conséquent, l’exemple de code peut interroger l’extension de type `ICustomLease` et vérifier la propriété `ICustomLease.IsIdle` dans l’état étendu.</span><span class="sxs-lookup"><span data-stu-id="969e9-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="969e9-150">Avant que la propriété `ICustomLease.IsIdle` soit activée, la propriété callback doit être définie comme ceci est essentiel pour que `CustomLeaseExtension` notifie le répartiteur lorsqu’il devient inactif.</span><span class="sxs-lookup"><span data-stu-id="969e9-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="969e9-151">Si `ICustomLease.IsIdle` retourne `true`, le membre privé `isIdle` reçoit simplement dans `CustomLifetimeLease` la valeur `true` et appelle la méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="969e9-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="969e9-152">Étant donné que le code contient un verrou, les autres threads ne peuvent pas modifier la valeur de ce membre privé.</span><span class="sxs-lookup"><span data-stu-id="969e9-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="969e9-153">Et la prochaine fois que le répartiteur appelle la <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, il retourne `true` et autorise le répartiteur à libérer l’instance.</span><span class="sxs-lookup"><span data-stu-id="969e9-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="969e9-154">Le travail préparatoire étant à présent terminé, l’extension personnalisée doit être raccordée au modèle de service.</span><span class="sxs-lookup"><span data-stu-id="969e9-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="969e9-155">Pour raccorder l’implémentation de `CustomLeaseExtension` au <xref:System.ServiceModel.InstanceContext>, WCF fournit l’interface <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> pour effectuer l’amorçage de <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="969e9-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="969e9-156">Dans l’exemple, la classe `CustomLeaseInitializer` implémente cette interface et ajoute une instance de `CustomLeaseExtension` à la collection <xref:System.ServiceModel.InstanceContext.Extensions%2A> à partir de la seule initialisation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="969e9-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="969e9-157">Cette méthode est appelée par le répartiteur en initialisant l'<xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="969e9-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="969e9-158">Enfin, l’implémentation de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est raccordée au modèle de service à l’aide de l’implémentation de <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="969e9-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="969e9-159">Cette implémentation est placée dans la classe `CustomLeaseTimeAttribute` et dérive également de la classe de base <xref:System.Attribute> pour exposer ce comportement en tant qu'attribut.</span><span class="sxs-lookup"><span data-stu-id="969e9-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="969e9-160">Ce comportement peut être ajouté à une classe de l'exemple de service en l'annotant avec l'attribut `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="969e9-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="969e9-161">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="969e9-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="969e9-162">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="969e9-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="969e9-163">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="969e9-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="969e9-164">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="969e9-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="969e9-165">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="969e9-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="969e9-166">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="969e9-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="969e9-167">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="969e9-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="969e9-168">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="969e9-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="969e9-169">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969e9-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="969e9-170">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="969e9-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
