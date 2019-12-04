---
title: Regroupement
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: d2962004376cf6f0752067d4e03828cd894efd01
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716516"
---
# <a name="pooling"></a><span data-ttu-id="08220-102">Regroupement</span><span class="sxs-lookup"><span data-stu-id="08220-102">Pooling</span></span>
<span data-ttu-id="08220-103">Cet exemple montre comment étendre Windows Communication Foundation (WCF) pour prendre en charge le regroupement d’objets.</span><span class="sxs-lookup"><span data-stu-id="08220-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="08220-104">L'exemple montre comment créer un attribut syntaxiquement et sémantiquement similaire aux fonctionnalités de l'attribut `ObjectPoolingAttribute` de Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="08220-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="08220-105">Le mise en pool d’objets permet une amélioration significative de la performance d'une application.</span><span class="sxs-lookup"><span data-stu-id="08220-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="08220-106">Toutefois, il peut avoir l'effet inverse s'il n'est pas utilisé de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="08220-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="08220-107">Le mise en pool d’objets évite d'avoir à recréer les objets fréquemment utilisés qui requièrent une initialisation complète.</span><span class="sxs-lookup"><span data-stu-id="08220-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="08220-108">Toutefois, si un appel à une méthode sur un objet du pool met beaucoup de temps à s'exécuter, le mise en pool d’objets met les demandes supplémentaires en file d'attente dès que la taille de pool maximale est atteinte.</span><span class="sxs-lookup"><span data-stu-id="08220-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="08220-109">Il peut donc ne pas traiter certaines demandes de création d'objet en levant une exception de délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="08220-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08220-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="08220-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="08220-111">La première étape de la création d’une extension WCF consiste à décider du point d’extensibilité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="08220-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="08220-112">Dans WCF, le terme *répartiteur* fait référence à un composant Runtime chargé de convertir les messages entrants en appels de méthode sur le service de l’utilisateur et de convertir les valeurs de retour de cette méthode en message sortant.</span><span class="sxs-lookup"><span data-stu-id="08220-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="08220-113">Un service WCF crée un répartiteur pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="08220-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="08220-114">Un client WCF doit utiliser un répartiteur si le contrat associé à ce client est un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="08220-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="08220-115">Les répartiteurs de canal et de point de terminaison offrent une extensibilité au niveau du contrat et du canal en exposant diverses propriétés qui contrôlent le comportement du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="08220-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="08220-116">La propriété <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> vous permet également d'inspecter, de modifier ou de personnaliser le processus de distribution.</span><span class="sxs-lookup"><span data-stu-id="08220-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="08220-117">Cet exemple se concentre sur la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> qui pointe sur l'objet qui fournit les instances de la classe de service.</span><span class="sxs-lookup"><span data-stu-id="08220-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="08220-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="08220-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="08220-119">Dans WCF, le répartiteur crée des instances de la classe de service à l’aide d’un <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, qui implémente l’interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider>.</span><span class="sxs-lookup"><span data-stu-id="08220-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="08220-120">Cette interface a trois méthodes :</span><span class="sxs-lookup"><span data-stu-id="08220-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="08220-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> : lorsqu'un message arrive, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> afin de créer une instance de la classe de service pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="08220-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="08220-122">La fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="08220-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="08220-123">Par exemple, si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall>, une nouvelle instance de classe de service est créée pour traiter chaque message qui arrive, et <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> est donc appelé chaque fois qu'un message arrive.</span><span class="sxs-lookup"><span data-stu-id="08220-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="08220-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29> : identique à la méthode précédente, excepté que celle-ci est appelée lorsqu'il n'y a pas d'argument Message.</span><span class="sxs-lookup"><span data-stu-id="08220-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="08220-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> : lorsque la durée de vie d'une instance de service a expiré, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="08220-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="08220-126">À l'instar de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, la fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="08220-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="08220-127">Mise en pool d’objets</span><span class="sxs-lookup"><span data-stu-id="08220-127">The Object Pool</span></span>  
 <span data-ttu-id="08220-128">Une implémentation <xref:System.ServiceModel.Dispatcher.IInstanceProvider> personnalisée fournit la sémantique de mise en pool d’objet requise pour un service.</span><span class="sxs-lookup"><span data-stu-id="08220-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="08220-129">Par conséquent, cet exemple a un type `ObjectPoolingInstanceProvider` qui fournit une implémentation personnalisée de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pour le pool.</span><span class="sxs-lookup"><span data-stu-id="08220-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="08220-130">Lorsque `Dispatcher` appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, au lieu de créer une instance, l'implémentation personnalisée recherche un objet existant dans un pool en mémoire.</span><span class="sxs-lookup"><span data-stu-id="08220-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="08220-131">Si aucun n'est disponible, il est retourné.</span><span class="sxs-lookup"><span data-stu-id="08220-131">If one is available, it is returned.</span></span> <span data-ttu-id="08220-132">Sinon, un nouvel objet est créé.</span><span class="sxs-lookup"><span data-stu-id="08220-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="08220-133">L'implémentation pour `GetInstance` est présentée dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="08220-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;            
}  
```  
  
 <span data-ttu-id="08220-134">L'implémentation `ReleaseInstance` personnalisée ajoute de nouveau l'instance libérée au pool et décrémente la valeur `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="08220-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="08220-135">`Dispatcher` peut appeler ces méthodes à partir de différents threads et, par conséquent, l’accès synchronisé aux membres au niveau de la classe dans la classe `ObjectPoolingInstanceProvider` est requis.</span><span class="sxs-lookup"><span data-stu-id="08220-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests   
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();                       
    }  
}  
```  
  
 <span data-ttu-id="08220-136">La méthode `ReleaseInstance` fournit une fonctionnalité « nettoyer l’initialisation ».</span><span class="sxs-lookup"><span data-stu-id="08220-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="08220-137">Normalement, le pool gère un nombre minimal d'objets pendant sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="08220-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="08220-138">Toutefois, il peut y avoir des périodes d'utilisation excessive qui requièrent la création d'objets supplémentaires dans le pool afin d'atteindre la limite maximale spécifiée dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="08220-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="08220-139">Par la suite, lorsque le pool devient moins actif, ces objets en surplus peuvent devenir une surcharge supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="08220-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="08220-140">Par conséquent, lorsque `activeObjectsCount` atteint zéro, une minuterie d'inactivité est démarrée, puis déclenche et effectue un cycle de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="08220-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="08220-141">Ajout du comportement</span><span class="sxs-lookup"><span data-stu-id="08220-141">Adding the Behavior</span></span>  
 <span data-ttu-id="08220-142">Les extensions de couche de répartiteur sont raccordées à l'aide des comportements suivants :</span><span class="sxs-lookup"><span data-stu-id="08220-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="08220-143">Comportements de service :</span><span class="sxs-lookup"><span data-stu-id="08220-143">Service Behaviors.</span></span> <span data-ttu-id="08220-144">permettent de personnaliser l'ensemble de l'exécution du service.</span><span class="sxs-lookup"><span data-stu-id="08220-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="08220-145">Comportements de point de terminaison :</span><span class="sxs-lookup"><span data-stu-id="08220-145">Endpoint Behaviors.</span></span> <span data-ttu-id="08220-146">permettent de personnaliser les points de terminaison de service, en particulier un répartiteur de canal et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="08220-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="08220-147">Comportements de contrat :</span><span class="sxs-lookup"><span data-stu-id="08220-147">Contract Behaviors.</span></span> <span data-ttu-id="08220-148">permettent de personnaliser les classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sur le client et le service, respectivement.</span><span class="sxs-lookup"><span data-stu-id="08220-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="08220-149">Dans le cadre d’une extension de mise en pool d’objets, vous devez créer un comportement de service.</span><span class="sxs-lookup"><span data-stu-id="08220-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="08220-150">Pour ce faire, implémentez l'interface <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="08220-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="08220-151">Il existe plusieurs méthodes pour que le modèle de service tienne compte des comportements personnalisés :</span><span class="sxs-lookup"><span data-stu-id="08220-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="08220-152">Utilisation d'un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08220-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="08220-153">L'ajouter de façon impérative à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="08220-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="08220-154">Extension du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="08220-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="08220-155">Cet exemple utilise un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08220-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="08220-156">Lorsque <xref:System.ServiceModel.ServiceHost> est construit, il examine les attributs utilisés dans la définition de type du service et ajoute les comportements disponibles à la collection de comportements de la description de service.</span><span class="sxs-lookup"><span data-stu-id="08220-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="08220-157">L'interface <xref:System.ServiceModel.Description.IServiceBehavior> a trois méthode : <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> et <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="08220-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="08220-158">La méthode <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> permet de s'assurer que le comportement peut être appliqué au service.</span><span class="sxs-lookup"><span data-stu-id="08220-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="08220-159">Dans cet exemple, l'implémentation garantit que le service n'est pas configuré avec <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="08220-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="08220-160">La méthode <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> permet de configurer les liaisons du service.</span><span class="sxs-lookup"><span data-stu-id="08220-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="08220-161">Elle n'est pas requise dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="08220-161">It is not required in this scenario.</span></span> <span data-ttu-id="08220-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> permet de configurer les répartiteurs du service.</span><span class="sxs-lookup"><span data-stu-id="08220-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="08220-163">Cette méthode est appelée par WCF lors de l’initialisation du <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="08220-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="08220-164">Les paramètres suivants sont passés dans cette méthode :</span><span class="sxs-lookup"><span data-stu-id="08220-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="08220-165">`Description` : cet argument fournit la description de service pour l'ensemble du service.</span><span class="sxs-lookup"><span data-stu-id="08220-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="08220-166">Il permet d’inspecter les données de description sur les points de terminaison, les contrats, les liaisons et autres données du service.</span><span class="sxs-lookup"><span data-stu-id="08220-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="08220-167">`ServiceHostBase`  cet argument fournit le <xref:System.ServiceModel.ServiceHostBase> actuellement initialisé.</span><span class="sxs-lookup"><span data-stu-id="08220-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="08220-168">Dans l'implémentation <xref:System.ServiceModel.Description.IServiceBehavior> personnalisée, une nouvelle instance de `ObjectPoolingInstanceProvider` est instanciée et assignée à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> dans chaque <xref:System.ServiceModel.Dispatcher.DispatchRuntime> de ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="08220-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,   
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior   
    // (this.throttlingBehavior==null), it should have initialized   
    // a single ServiceThrottle on all ChannelDispatchers.    
    // As we loop through the ChannelDispatchers, we verify that   
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in   
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all   
            // endpoints. If there were others, we could not enforce   
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&   
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new   
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =   
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items   
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >   
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="08220-169">Outre une implémentation <xref:System.ServiceModel.Description.IServiceBehavior>, la classe <xref:System.EnterpriseServices.ObjectPoolingAttribute> a plusieurs membres pour personnaliser le mise en pool d’objets à l’aide des arguments d’attribut.</span><span class="sxs-lookup"><span data-stu-id="08220-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="08220-170">Ces membres incluent <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> et <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, pour faire correspondre le jeu de fonctionnalités de mise en pool d’objets fourni par .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="08220-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="08220-171">Le comportement de mise en pool d’objets peut maintenant être ajouté à un service WCF en annotant l’implémentation de service avec l’attribut de `ObjectPooling` personnalisé récemment créé.</span><span class="sxs-lookup"><span data-stu-id="08220-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="08220-172">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="08220-172">Running the Sample</span></span>  
 <span data-ttu-id="08220-173">L'exemple montre les avantages qui peuvent être retirés en termes de performance en utilisant le mise en pool d’objets dans des scénarios spécifiques.</span><span class="sxs-lookup"><span data-stu-id="08220-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="08220-174">L'application de service implémente deux services : `WorkService` et `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="08220-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="08220-175">Ces deux services partagent la même implémentation : ils requièrent tous deux une initialisation gourmande en ressources, puis exposent une méthode `DoWork()` qui s'avère relativement peu gourmande.</span><span class="sxs-lookup"><span data-stu-id="08220-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="08220-176">La seule différence est que le mise en pool d’objets de `ObjectPooledWorkService` est configuré :</span><span class="sxs-lookup"><span data-stu-id="08220-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }          
}  
```  
  
 <span data-ttu-id="08220-177">Lorsque vous exécutez le client, il chronomètre l'appel à `WorkService` 5 fois.</span><span class="sxs-lookup"><span data-stu-id="08220-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="08220-178">Il chronomètre ensuite l'appel à `ObjectPooledWorkService` 5 fois.</span><span class="sxs-lookup"><span data-stu-id="08220-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="08220-179">La différence de temps est ensuite affichée :</span><span class="sxs-lookup"><span data-stu-id="08220-179">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="08220-180">La première fois que le client est exécuté, les deux services semblent prendre environ le même temps.</span><span class="sxs-lookup"><span data-stu-id="08220-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="08220-181">Si vous ré-exécutez l'exemple, vous constatez que `ObjectPooledWorkService` retourne beaucoup plus rapidement car une instance de cet objet existe déjà dans le pool.</span><span class="sxs-lookup"><span data-stu-id="08220-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08220-182">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="08220-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="08220-183">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08220-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="08220-184">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08220-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="08220-185">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08220-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08220-186">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="08220-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08220-187">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="08220-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08220-188">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="08220-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="08220-189">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08220-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08220-190">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="08220-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
