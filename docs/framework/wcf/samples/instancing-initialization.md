---
title: Instancing Initialization
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 06a8dfe571b652ded236df3097b37861c03a858d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596654"
---
# <a name="instancing-initialization"></a><span data-ttu-id="95efd-102">Instancing Initialization</span><span class="sxs-lookup"><span data-stu-id="95efd-102">Instancing Initialization</span></span>
<span data-ttu-id="95efd-103">Cet exemple étend l’exemple de [regroupement](pooling.md) en définissant une interface, `IObjectControl` , qui personnalise l’initialisation d’un objet en l’activant et en le désactivant.</span><span class="sxs-lookup"><span data-stu-id="95efd-103">This sample extends the [Pooling](pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="95efd-104">Le client appelle des méthodes qui retournent l'objet au pool et d'autres qui ne retournent pas l'objet au pool.</span><span class="sxs-lookup"><span data-stu-id="95efd-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95efd-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="95efd-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="95efd-106">Points d'extensibilité</span><span class="sxs-lookup"><span data-stu-id="95efd-106">Extensibility Points</span></span>  
 <span data-ttu-id="95efd-107">La première étape de la création d’une extension Windows Communication Foundation (WCF) consiste à décider du point d’extensibilité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="95efd-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="95efd-108">Dans WCF, le terme *EndpointDispatcher* fait référence à un composant Runtime chargé de convertir des messages entrants en appels de méthode sur le service de l’utilisateur et de convertir les valeurs de retour de cette méthode en message sortant.</span><span class="sxs-lookup"><span data-stu-id="95efd-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="95efd-109">Un service WCF crée un EndpointDispatcher pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="95efd-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="95efd-110">L'EndpointDispatcher permet l'extensibilité de l'étendue du point de terminaison (pour tous les messages reçus ou envoyés par le service) à l'aide de la classe <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="95efd-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="95efd-111">Cette classe vous permet de personnaliser différentes propriétés qui contrôlent le comportement de l'EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="95efd-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="95efd-112">Cet exemple se concentre sur la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> qui pointe sur l'objet qui fournit les instances de la classe de service.</span><span class="sxs-lookup"><span data-stu-id="95efd-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="95efd-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="95efd-113">IInstanceProvider</span></span>  
 <span data-ttu-id="95efd-114">Dans WCF, EndpointDispatcher crée des instances d’une classe de service à l’aide d’un fournisseur d’instances qui implémente l' <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span><span class="sxs-lookup"><span data-stu-id="95efd-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="95efd-115">Cette interface possède uniquement deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="95efd-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="95efd-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> : lorsqu'un message arrive, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> afin de créer une instance de la classe de service pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="95efd-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="95efd-117">La fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="95efd-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="95efd-118">Par exemple, si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, une nouvelle instance de la classe de service est créée pour traiter chaque message qui arrive, et <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> est donc appelée chaque fois qu'un message arrive.</span><span class="sxs-lookup"><span data-stu-id="95efd-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="95efd-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> : lorsque l'instance de service finit de traiter le message, l'EndpointDispatcher appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="95efd-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="95efd-120">À l'instar de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, la fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="95efd-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="95efd-121">Mise en pool d’objets</span><span class="sxs-lookup"><span data-stu-id="95efd-121">The Object Pool</span></span>  
 <span data-ttu-id="95efd-122">La classe `ObjectPoolInstanceProvider` contient l'implémentation pour le mise en pool d’objets.</span><span class="sxs-lookup"><span data-stu-id="95efd-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="95efd-123">Cette classe implémente l'interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pour interagir avec la couche de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="95efd-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="95efd-124">Lorsque l'EndpointDispatcher appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, au lieu de créer une instance, l'implémentation personnalisée recherche un objet existant dans un pool en mémoire.</span><span class="sxs-lookup"><span data-stu-id="95efd-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="95efd-125">Si aucun n'est disponible, il est retourné.</span><span class="sxs-lookup"><span data-stu-id="95efd-125">If one is available, it is returned.</span></span> <span data-ttu-id="95efd-126">Sinon, `ObjectPoolInstanceProvider` vérifie si la propriété `ActiveObjectsCount` (nombre d'objets retournés depuis le pool) a atteint la taille de pool maximale.</span><span class="sxs-lookup"><span data-stu-id="95efd-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="95efd-127">Si ce n'est pas le cas, une nouvelle instance est créée et retournée à l'appelant et `ActiveObjectsCount` est incrémenté par la suite.</span><span class="sxs-lookup"><span data-stu-id="95efd-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="95efd-128">Sinon, une demande de création d'objet est mise en file d'attente pendant le laps de temps configuré.</span><span class="sxs-lookup"><span data-stu-id="95efd-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="95efd-129">L'implémentation pour `GetObjectFromThePool` est présentée dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="95efd-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="95efd-130">L'implémentation `ReleaseInstance` personnalisée ajoute de nouveau l'instance libérée au pool et décrémente la valeur `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="95efd-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="95efd-131">L’EndpointDispatcher peut appeler ces méthodes à partir de différents threads et, par conséquent, l’accès synchronisé aux membres au niveau de la classe dans la classe `ObjectPoolInstanceProvider` est requis.</span><span class="sxs-lookup"><span data-stu-id="95efd-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="95efd-132">La `ReleaseInstance` méthode fournit une fonctionnalité *d’initialisation de nettoyage* .</span><span class="sxs-lookup"><span data-stu-id="95efd-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="95efd-133">Normalement, le pool gère un nombre minimal d'objets pendant sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="95efd-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="95efd-134">Toutefois, il peut y avoir des périodes d'utilisation excessive qui requièrent la création d'objets supplémentaires dans le pool afin d'atteindre la limite maximale spécifiée dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="95efd-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="95efd-135">Par la suite, lorsque le pool devient moins actif, ces objets en surplus peuvent devenir une surcharge supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="95efd-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="95efd-136">Par conséquent, lorsque le `activeObjectsCount` atteint zéro, une minuterie d'inactivité est démarrée, qui déclenche et effectue un cycle de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="95efd-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="95efd-137">Les extensions de couche ServiceModel sont raccordées à l’aide des comportements suivants :</span><span class="sxs-lookup"><span data-stu-id="95efd-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="95efd-138">Comportements de service : permettent de personnaliser l'ensemble de l'exécution du service.</span><span class="sxs-lookup"><span data-stu-id="95efd-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="95efd-139">Comportements de point de terminaison : permettent de personnaliser un point de terminaison de service particulier, y compris l'EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="95efd-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="95efd-140">Comportements de contrat : permettent de personnaliser la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> ou la classe <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sur le client ou le service respectivement.</span><span class="sxs-lookup"><span data-stu-id="95efd-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="95efd-141">Comportements d'opération : permettent de personnaliser la classe <xref:System.ServiceModel.Dispatcher.ClientOperation> ou la classe <xref:System.ServiceModel.Dispatcher.DispatchOperation> sur le client ou le service respectivement.</span><span class="sxs-lookup"><span data-stu-id="95efd-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="95efd-142">Dans le cadre d’une extension de mise en pool d’objets, il est possible de créer un comportement de point de terminaison ou un comportement de service.</span><span class="sxs-lookup"><span data-stu-id="95efd-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="95efd-143">Dans cet exemple, nous utilisons un comportement de service qui applique la capacité de mise en mise en pool d’objets à chaque point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="95efd-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="95efd-144">Pour ce faire, implémentez l'interface <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="95efd-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="95efd-145">Il existe plusieurs méthodes pour que le ServiceModel tienne compte des comportements personnalisés :</span><span class="sxs-lookup"><span data-stu-id="95efd-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="95efd-146">Utilisation d'un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95efd-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="95efd-147">L'ajouter de façon impérative à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="95efd-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="95efd-148">Extension du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="95efd-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="95efd-149">Cet exemple utilise un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95efd-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="95efd-150">Lorsque <xref:System.ServiceModel.ServiceHost> est généré, il examine les attributs utilisés dans la définition de type du service et ajoute les comportements disponibles à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="95efd-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="95efd-151">L' <xref:System.ServiceModel.Description.IServiceBehavior> interface a trois méthodes : <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` et <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> .</span><span class="sxs-lookup"><span data-stu-id="95efd-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="95efd-152">Ces méthodes sont appelées par WCF lorsque le <xref:System.ServiceModel.ServiceHost> est en cours d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="95efd-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="95efd-153">l'<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> est appelée en premier ; elle autorise l'inspection du service pour retrouver les éventuelles incohérences.</span><span class="sxs-lookup"><span data-stu-id="95efd-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="95efd-154">l'<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> est appelée ensuite ; cette méthode est requise uniquement dans les scénarios très avancés.</span><span class="sxs-lookup"><span data-stu-id="95efd-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="95efd-155">l'<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> est appelée en dernier ; elle est responsable de la configuration de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="95efd-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="95efd-156">Les paramètres suivants sont passés dans <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="95efd-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="95efd-157">`Description` : ce paramètre fournit la description de service pour le service entier.</span><span class="sxs-lookup"><span data-stu-id="95efd-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="95efd-158">Il permet d’inspecter les données de description des points de terminaison, des contrats et des liaisons, et les autres données associées au service.</span><span class="sxs-lookup"><span data-stu-id="95efd-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="95efd-159">`ServiceHostBase` : ce paramètre fournit le <xref:System.ServiceModel.ServiceHostBase> en cours d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="95efd-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="95efd-160">Dans l'implémentation <xref:System.ServiceModel.Description.IServiceBehavior> personnalisée, une nouvelle instance du `ObjectPoolInstanceProvider` est instanciée et assignée à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> dans chaque <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> joint au <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="95efd-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}
```  
  
 <span data-ttu-id="95efd-161">Outre une implémentation <xref:System.ServiceModel.Description.IServiceBehavior>, la classe `ObjectPoolingAttribute` a plusieurs membres pour personnaliser le mise en pool d’objets à l’aide des arguments d’attribut.</span><span class="sxs-lookup"><span data-stu-id="95efd-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="95efd-162">Ces membres incluent `MaxSize`, `MinSize`, `Enabled` et `CreationTimeout`, pour faire correspondre le jeu de fonctionnalités de mise en mise en pool d’objets fourni par .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="95efd-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="95efd-163">Le comportement de mise en pool d’objets peut maintenant être ajouté à un service WCF en annotant l’implémentation de service avec l’attribut personnalisé nouvellement créé `ObjectPooling` .</span><span class="sxs-lookup"><span data-stu-id="95efd-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="95efd-164">Activation et désactivation du raccordement</span><span class="sxs-lookup"><span data-stu-id="95efd-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="95efd-165">L'objectif principal de la mise en mise en pool d’objets est d'optimiser la création et l'initialisation relativement coûteuses des objets éphémères.</span><span class="sxs-lookup"><span data-stu-id="95efd-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="95efd-166">Par conséquent, elle peut singulièrement améliorer les performances d'une application si elle est utilisée correctement.</span><span class="sxs-lookup"><span data-stu-id="95efd-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="95efd-167">Étant donné que l'objet est retourné depuis le pool, le constructeur est appelé une seule fois.</span><span class="sxs-lookup"><span data-stu-id="95efd-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="95efd-168">Toutefois, certaines applications requièrent un certain niveau de contrôle afin de pouvoir initialiser et nettoyer les ressources utilisées dans un contexte unique.</span><span class="sxs-lookup"><span data-stu-id="95efd-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="95efd-169">Par exemple, un objet utilisé pour un ensemble de calculs peut réinitialiser ses champs privés avant de traiter le calcul suivant.</span><span class="sxs-lookup"><span data-stu-id="95efd-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="95efd-170">Les Enterprise Services ont activé ce type d'initialisation spécifique au contexte en laissant le développeur d'objets substituer les méthodes `Activate` et `Deactivate` de la classe <xref:System.EnterpriseServices.ServicedComponent> de base.</span><span class="sxs-lookup"><span data-stu-id="95efd-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="95efd-171">Le pool d'objets appelle la méthode `Activate` juste avant de retourner l'objet depuis le pool.</span><span class="sxs-lookup"><span data-stu-id="95efd-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="95efd-172">`Deactivate` est appelé lorsque l'objet est retourné au pool.</span><span class="sxs-lookup"><span data-stu-id="95efd-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="95efd-173">La classe <xref:System.EnterpriseServices.ServicedComponent> de base a également une propriété `boolean` appelée `CanBePooled`, qui peut être utilisée pour notifier au pool que l'objet peut être davantage regroupé.</span><span class="sxs-lookup"><span data-stu-id="95efd-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="95efd-174">Pour reproduire ces fonctionnalités, l'exemple déclare une interface publique (`IObjectControl`) avec les membres susmentionnés.</span><span class="sxs-lookup"><span data-stu-id="95efd-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="95efd-175">Puis cette interface est implémentée par les classes de service conçues pour assurer l'initialisation spécifique au contexte.</span><span class="sxs-lookup"><span data-stu-id="95efd-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="95efd-176">L’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceProvider> doit être modifiée pour satisfaire ces exigences.</span><span class="sxs-lookup"><span data-stu-id="95efd-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="95efd-177">À présent, chaque fois que vous récupérez un objet en appelant la `GetInstance` méthode, vous devez vérifier si l’objet implémente `IObjectControl.` , si c’est le cas, vous devez appeler la `Activate` méthode de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="95efd-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="95efd-178">Lors du retour d'un objet au pool, un contrôle de la propriété `CanBePooled` est requis avant d'ajouter de nouveau l'objet au pool.</span><span class="sxs-lookup"><span data-stu-id="95efd-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="95efd-179">Vu que le développeur de service peut décider si un objet peut être regroupé ou non, le nombre d'objets dans le pool à un moment donné peut être inférieur à la taille minimale.</span><span class="sxs-lookup"><span data-stu-id="95efd-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="95efd-180">Par conséquent, vous devez vérifier si le nombre d'objets est inférieur au minimum et effectuer l'initialisation nécessaire dans la procédure de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="95efd-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="95efd-181">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="95efd-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="95efd-182">Appuyez sur Enter dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="95efd-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95efd-183">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="95efd-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="95efd-184">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95efd-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="95efd-185">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95efd-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="95efd-186">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95efd-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="95efd-187">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95efd-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95efd-188">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="95efd-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="95efd-189">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="95efd-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95efd-190">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="95efd-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
