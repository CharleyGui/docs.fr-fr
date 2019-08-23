---
title: Instancing Initialization
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: f97a8b6723224b73476f84703ec3975abff0b476
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931036"
---
# <a name="instancing-initialization"></a><span data-ttu-id="789b3-102">Instancing Initialization</span><span class="sxs-lookup"><span data-stu-id="789b3-102">Instancing Initialization</span></span>
<span data-ttu-id="789b3-103">Cet exemple étend l’exemple de [regroupement](../../../../docs/framework/wcf/samples/pooling.md) en définissant une interface `IObjectControl`,, qui personnalise l’initialisation d’un objet en l’activant et en le désactivant.</span><span class="sxs-lookup"><span data-stu-id="789b3-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="789b3-104">Le client appelle des méthodes qui retournent l'objet au pool et d'autres qui ne retournent pas l'objet au pool.</span><span class="sxs-lookup"><span data-stu-id="789b3-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="789b3-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="789b3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="789b3-106">Points d'extensibilité</span><span class="sxs-lookup"><span data-stu-id="789b3-106">Extensibility Points</span></span>  
 <span data-ttu-id="789b3-107">La première étape de la création d’une extension Windows Communication Foundation (WCF) consiste à décider du point d’extensibilité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="789b3-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="789b3-108">Dans WCF, le terme *EndpointDispatcher* fait référence à un composant Runtime chargé de convertir des messages entrants en appels de méthode sur le service de l’utilisateur et de convertir les valeurs de retour de cette méthode en message sortant.</span><span class="sxs-lookup"><span data-stu-id="789b3-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="789b3-109">Un service WCF crée un EndpointDispatcher pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="789b3-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="789b3-110">L'EndpointDispatcher permet l'extensibilité de l'étendue du point de terminaison (pour tous les messages reçus ou envoyés par le service) à l'aide de la classe <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="789b3-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="789b3-111">Cette classe vous permet de personnaliser différentes propriétés qui contrôlent le comportement de l'EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="789b3-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="789b3-112">Cet exemple se concentre sur la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> qui pointe sur l'objet qui fournit les instances de la classe de service.</span><span class="sxs-lookup"><span data-stu-id="789b3-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="789b3-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="789b3-113">IInstanceProvider</span></span>  
 <span data-ttu-id="789b3-114">Dans WCF, EndpointDispatcher crée des instances d’une classe de service à l’aide d’un fournisseur d’instances <xref:System.ServiceModel.Dispatcher.IInstanceProvider> qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="789b3-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="789b3-115">Cette interface possède uniquement deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="789b3-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="789b3-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Lorsqu’un message arrive, le répartiteur appelle la <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> méthode pour créer une instance de la classe de service pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="789b3-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="789b3-117">La fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="789b3-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="789b3-118">Par exemple, si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, une nouvelle instance de la classe de service est créée pour traiter chaque message qui arrive, et <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> est donc appelée chaque fois qu'un message arrive.</span><span class="sxs-lookup"><span data-stu-id="789b3-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="789b3-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Lorsque l’instance de service finit de traiter le message, EndpointDispatcher appelle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> la méthode.</span><span class="sxs-lookup"><span data-stu-id="789b3-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="789b3-120">À l'instar de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, la fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="789b3-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="789b3-121">Mise en pool d’objets</span><span class="sxs-lookup"><span data-stu-id="789b3-121">The Object Pool</span></span>  
 <span data-ttu-id="789b3-122">La classe `ObjectPoolInstanceProvider` contient l'implémentation pour le mise en pool d’objets.</span><span class="sxs-lookup"><span data-stu-id="789b3-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="789b3-123">Cette classe implémente l'interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pour interagir avec la couche de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="789b3-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="789b3-124">Lorsque l'EndpointDispatcher appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, au lieu de créer une instance, l'implémentation personnalisée recherche un objet existant dans un pool en mémoire.</span><span class="sxs-lookup"><span data-stu-id="789b3-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="789b3-125">Si aucun n'est disponible, il est retourné.</span><span class="sxs-lookup"><span data-stu-id="789b3-125">If one is available, it is returned.</span></span> <span data-ttu-id="789b3-126">Sinon, `ObjectPoolInstanceProvider` vérifie si la propriété `ActiveObjectsCount` (nombre d'objets retournés depuis le pool) a atteint la taille de pool maximale.</span><span class="sxs-lookup"><span data-stu-id="789b3-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="789b3-127">Si ce n'est pas le cas, une nouvelle instance est créée et retournée à l'appelant et `ActiveObjectsCount` est incrémenté par la suite.</span><span class="sxs-lookup"><span data-stu-id="789b3-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="789b3-128">Sinon, une demande de création d'objet est mise en file d'attente pendant le laps de temps configuré.</span><span class="sxs-lookup"><span data-stu-id="789b3-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="789b3-129">L'implémentation pour `GetObjectFromThePool` est présentée dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="789b3-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="789b3-130">L'implémentation `ReleaseInstance` personnalisée ajoute de nouveau l'instance libérée au pool et décrémente la valeur `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="789b3-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="789b3-131">L’EndpointDispatcher peut appeler ces méthodes à partir de différents threads et, par conséquent, l’accès synchronisé aux membres au niveau de la classe dans la classe `ObjectPoolInstanceProvider` est requis.</span><span class="sxs-lookup"><span data-stu-id="789b3-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```  
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
  
 <span data-ttu-id="789b3-132">La `ReleaseInstance` méthode fournit une fonctionnalité *d’initialisation de nettoyage* .</span><span class="sxs-lookup"><span data-stu-id="789b3-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="789b3-133">Normalement, le pool gère un nombre minimal d'objets pendant sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="789b3-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="789b3-134">Toutefois, il peut y avoir des périodes d'utilisation excessive qui requièrent la création d'objets supplémentaires dans le pool afin d'atteindre la limite maximale spécifiée dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="789b3-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="789b3-135">Par la suite, lorsque le pool devient moins actif, ces objets en surplus peuvent devenir une surcharge supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="789b3-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="789b3-136">Par conséquent, lorsque le `activeObjectsCount` atteint zéro, une minuterie d'inactivité est démarrée, qui déclenche et effectue un cycle de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="789b3-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="789b3-137">Les extensions de couche ServiceModel sont raccordées à l’aide des comportements suivants :</span><span class="sxs-lookup"><span data-stu-id="789b3-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="789b3-138">Comportements de service: permettent de personnaliser l'ensemble de l'exécution du service.</span><span class="sxs-lookup"><span data-stu-id="789b3-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="789b3-139">Comportements des points de terminaison: Celles-ci permettent la personnalisation d’un point de terminaison de service particulier, y compris EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="789b3-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="789b3-140">Comportements de contrat: Celles-ci permettent la personnalisation des <xref:System.ServiceModel.Dispatcher.ClientRuntime> classes ou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sur le client ou le service, respectivement.</span><span class="sxs-lookup"><span data-stu-id="789b3-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="789b3-141">Comportements de l’opération: Celles-ci permettent la personnalisation des <xref:System.ServiceModel.Dispatcher.ClientOperation> classes ou <xref:System.ServiceModel.Dispatcher.DispatchOperation> sur le client ou le service, respectivement.</span><span class="sxs-lookup"><span data-stu-id="789b3-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="789b3-142">Dans le cadre d’une extension de mise en pool d’objets, il est possible de créer un comportement de point de terminaison ou un comportement de service.</span><span class="sxs-lookup"><span data-stu-id="789b3-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="789b3-143">Dans cet exemple, nous utilisons un comportement de service qui applique la capacité de mise en mise en pool d’objets à chaque point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="789b3-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="789b3-144">Pour ce faire, implémentez l'interface <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="789b3-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="789b3-145">Il existe plusieurs méthodes pour que le ServiceModel tienne compte des comportements personnalisés :</span><span class="sxs-lookup"><span data-stu-id="789b3-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="789b3-146">Utilisation d'un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="789b3-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="789b3-147">L'ajouter de façon impérative à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="789b3-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="789b3-148">Extension du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="789b3-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="789b3-149">Cet exemple utilise un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="789b3-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="789b3-150">Lorsque <xref:System.ServiceModel.ServiceHost> est généré, il examine les attributs utilisés dans la définition de type du service et ajoute les comportements disponibles à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="789b3-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="789b3-151">L' <xref:System.ServiceModel.Description.IServiceBehavior> interface a trois méthodes: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> et.`,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="789b3-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="789b3-152">Ces méthodes sont appelées par WCF lorsque <xref:System.ServiceModel.ServiceHost> le est en cours d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="789b3-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="789b3-153">l'<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> est appelée en premier ; elle autorise l'inspection du service pour retrouver les éventuelles incohérences.</span><span class="sxs-lookup"><span data-stu-id="789b3-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="789b3-154">l'<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> est appelée ensuite ; cette méthode est requise uniquement dans les scénarios très avancés.</span><span class="sxs-lookup"><span data-stu-id="789b3-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="789b3-155">l'<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> est appelée en dernier ; elle est responsable de la configuration de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="789b3-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="789b3-156">Les paramètres suivants sont passés dans <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="789b3-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="789b3-157">`Description`: Ce paramètre fournit la description de service pour l’ensemble du service.</span><span class="sxs-lookup"><span data-stu-id="789b3-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="789b3-158">Il permet d’inspecter les données de description des points de terminaison, des contrats et des liaisons, et les autres données associées au service.</span><span class="sxs-lookup"><span data-stu-id="789b3-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="789b3-159">`ServiceHostBase`: Ce paramètre fournit le <xref:System.ServiceModel.ServiceHostBase> qui est actuellement initialisé.</span><span class="sxs-lookup"><span data-stu-id="789b3-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="789b3-160">Dans l'implémentation <xref:System.ServiceModel.Description.IServiceBehavior> personnalisée, une nouvelle instance du `ObjectPoolInstanceProvider` est instanciée et assignée à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> dans chaque <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> joint au <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="789b3-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```  
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
  
 <span data-ttu-id="789b3-161">Outre une implémentation <xref:System.ServiceModel.Description.IServiceBehavior>, la classe `ObjectPoolingAttribute` a plusieurs membres pour personnaliser le mise en pool d’objets à l’aide des arguments d’attribut.</span><span class="sxs-lookup"><span data-stu-id="789b3-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="789b3-162">Ces membres incluent `MaxSize`, `MinSize`, `Enabled` et `CreationTimeout`, pour faire correspondre le jeu de fonctionnalités de mise en mise en pool d’objets fourni par .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="789b3-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="789b3-163">Le comportement de mise en pool d’objets peut maintenant être ajouté à un service WCF en annotant l’implémentation de service `ObjectPooling` avec l’attribut personnalisé nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="789b3-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="789b3-164">Activation et désactivation du raccordement</span><span class="sxs-lookup"><span data-stu-id="789b3-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="789b3-165">L'objectif principal de la mise en mise en pool d’objets est d'optimiser la création et l'initialisation relativement coûteuses des objets éphémères.</span><span class="sxs-lookup"><span data-stu-id="789b3-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="789b3-166">Par conséquent, elle peut singulièrement améliorer les performances d'une application si elle est utilisée correctement.</span><span class="sxs-lookup"><span data-stu-id="789b3-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="789b3-167">Étant donné que l'objet est retourné depuis le pool, le constructeur est appelé une seule fois.</span><span class="sxs-lookup"><span data-stu-id="789b3-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="789b3-168">Toutefois, certaines applications requièrent un certain niveau de contrôle afin de pouvoir initialiser et nettoyer les ressources utilisées dans un contexte unique.</span><span class="sxs-lookup"><span data-stu-id="789b3-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="789b3-169">Par exemple, un objet utilisé pour un ensemble de calculs peut réinitialiser ses champs privés avant de traiter le calcul suivant.</span><span class="sxs-lookup"><span data-stu-id="789b3-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="789b3-170">Les Enterprise Services ont activé ce type d'initialisation spécifique au contexte en laissant le développeur d'objets substituer les méthodes `Activate` et `Deactivate` de la classe <xref:System.EnterpriseServices.ServicedComponent> de base.</span><span class="sxs-lookup"><span data-stu-id="789b3-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="789b3-171">Le pool d'objets appelle la méthode `Activate` juste avant de retourner l'objet depuis le pool.</span><span class="sxs-lookup"><span data-stu-id="789b3-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="789b3-172">`Deactivate` est appelé lorsque l'objet est retourné au pool.</span><span class="sxs-lookup"><span data-stu-id="789b3-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="789b3-173">La classe <xref:System.EnterpriseServices.ServicedComponent> de base a également une propriété `boolean` appelée `CanBePooled`, qui peut être utilisée pour notifier au pool que l'objet peut être davantage regroupé.</span><span class="sxs-lookup"><span data-stu-id="789b3-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="789b3-174">Pour reproduire ces fonctionnalités, l'exemple déclare une interface publique (`IObjectControl`) avec les membres susmentionnés.</span><span class="sxs-lookup"><span data-stu-id="789b3-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="789b3-175">Puis cette interface est implémentée par les classes de service conçues pour assurer l'initialisation spécifique au contexte.</span><span class="sxs-lookup"><span data-stu-id="789b3-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="789b3-176">L’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceProvider> doit être modifiée pour satisfaire ces exigences.</span><span class="sxs-lookup"><span data-stu-id="789b3-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="789b3-177">À présent, chaque fois que vous récupérez un objet `GetInstance` en appelant la méthode, vous devez vérifier si l' `IObjectControl.` objet implémente, si c’est le `Activate` cas, vous devez appeler la méthode de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="789b3-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="789b3-178">Lors du retour d'un objet au pool, un contrôle de la propriété `CanBePooled` est requis avant d'ajouter de nouveau l'objet au pool.</span><span class="sxs-lookup"><span data-stu-id="789b3-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```  
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
  
 <span data-ttu-id="789b3-179">Vu que le développeur de service peut décider si un objet peut être regroupé ou non, le nombre d'objets dans le pool à un moment donné peut être inférieur à la taille minimale.</span><span class="sxs-lookup"><span data-stu-id="789b3-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="789b3-180">Par conséquent, vous devez vérifier si le nombre d'objets est inférieur au minimum et effectuer l'initialisation nécessaire dans la procédure de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="789b3-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```  
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
  
 <span data-ttu-id="789b3-181">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="789b3-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="789b3-182">Appuyez sur Enter dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="789b3-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="789b3-183">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="789b3-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="789b3-184">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="789b3-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="789b3-185">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="789b3-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="789b3-186">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="789b3-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="789b3-187">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="789b3-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="789b3-188">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="789b3-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="789b3-189">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="789b3-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="789b3-190">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="789b3-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
