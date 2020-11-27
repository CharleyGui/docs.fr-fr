---
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 6b266dafa945fa44d6c857810df42eb5439f157d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255427"
---
# <a name="pooling"></a>Pooling

Cet exemple montre comment étendre Windows Communication Foundation (WCF) pour prendre en charge le regroupement d’objets. L'exemple montre comment créer un attribut syntaxiquement et sémantiquement similaire aux fonctionnalités de l'attribut `ObjectPoolingAttribute` de Enterprise Services. Le mise en pool d’objets permet une amélioration significative de la performance d'une application. Toutefois, il peut avoir l'effet inverse s'il n'est pas utilisé de manière appropriée. Le mise en pool d’objets évite d'avoir à recréer les objets fréquemment utilisés qui requièrent une initialisation complète. Toutefois, si un appel à une méthode sur un objet du pool met beaucoup de temps à s'exécuter, le mise en pool d’objets met les demandes supplémentaires en file d'attente dès que la taille de pool maximale est atteinte. Il peut donc ne pas traiter certaines demandes de création d'objet en levant une exception de délai d'attente.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La première étape de la création d’une extension WCF consiste à décider du point d’extensibilité à utiliser.  
  
 Dans WCF, le terme *répartiteur* fait référence à un composant Runtime chargé de convertir les messages entrants en appels de méthode sur le service de l’utilisateur et de convertir les valeurs de retour de cette méthode en message sortant. Un service WCF crée un répartiteur pour chaque point de terminaison. Un client WCF doit utiliser un répartiteur si le contrat associé à ce client est un contrat duplex.  
  
 Les répartiteurs de canal et de point de terminaison offrent une extensibilité au niveau du contrat et du canal en exposant diverses propriétés qui contrôlent le comportement du répartiteur. La propriété <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> vous permet également d'inspecter, de modifier ou de personnaliser le processus de distribution. Cet exemple se concentre sur la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> qui pointe sur l'objet qui fournit les instances de la classe de service.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  

 Dans WCF, le répartiteur crée des instances de la classe de service à l’aide d’un <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> , qui implémente l' <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface. Cette interface a trois méthodes :  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> : lorsqu'un message arrive, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> afin de créer une instance de la classe de service pour traiter le message. La fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Par exemple, si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall>, une nouvelle instance de classe de service est créée pour traiter chaque message qui arrive, et <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> est donc appelé chaque fois qu'un message arrive.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29> : identique à la méthode précédente, excepté que celle-ci est appelée lorsqu'il n'y a pas d'argument Message.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> : lorsque la durée de vie d'une instance de service a expiré, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>. À l'instar de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, la fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Mise en pool d’objets  

 Une implémentation <xref:System.ServiceModel.Dispatcher.IInstanceProvider> personnalisée fournit la sémantique de mise en pool d’objet requise pour un service. Par conséquent, cet exemple a un type `ObjectPoolingInstanceProvider` qui fournit une implémentation personnalisée de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pour le pool. Lorsque `Dispatcher` appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, au lieu de créer une instance, l'implémentation personnalisée recherche un objet existant dans un pool en mémoire. Si aucun n'est disponible, il est retourné. Sinon, un nouvel objet est créé. L'implémentation pour `GetInstance` est présentée dans l'exemple de code suivant.  
  
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
  
 L'implémentation `ReleaseInstance` personnalisée ajoute de nouveau l'instance libérée au pool et décrémente la valeur `ActiveObjectsCount`. `Dispatcher` peut appeler ces méthodes à partir de différents threads et, par conséquent, l’accès synchronisé aux membres au niveau de la classe dans la classe `ObjectPoolingInstanceProvider` est requis.  
  
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
  
 La `ReleaseInstance` méthode fournit une fonctionnalité « nettoyer l’initialisation ». Normalement, le pool gère un nombre minimal d'objets pendant sa durée de vie. Toutefois, il peut y avoir des périodes d'utilisation excessive qui requièrent la création d'objets supplémentaires dans le pool afin d'atteindre la limite maximale spécifiée dans la configuration. Par la suite, lorsque le pool devient moins actif, ces objets en surplus peuvent devenir une surcharge supplémentaire. Par conséquent, lorsque `activeObjectsCount` atteint zéro, une minuterie d'inactivité est démarrée, puis déclenche et effectue un cycle de nettoyage.  
  
## <a name="adding-the-behavior"></a>Ajout du comportement  

 Les extensions de couche de répartiteur sont raccordées à l'aide des comportements suivants :  
  
- Comportements de service : permettent de personnaliser l'ensemble de l'exécution du service.  
  
- Comportements de point de terminaison : permettent de personnaliser les points de terminaison de service, en particulier un répartiteur de canal et de point de terminaison.  
  
- Comportements de contrat : permettent de personnaliser les classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sur le client et le service, respectivement.  
  
 Dans le cadre d’une extension de mise en pool d’objets, vous devez créer un comportement de service. Pour ce faire, implémentez l'interface <xref:System.ServiceModel.Description.IServiceBehavior>. Il existe plusieurs méthodes pour que le modèle de service tienne compte des comportements personnalisés :  
  
- Utilisation d'un attribut personnalisé.  
  
- L'ajouter de façon impérative à la collection de comportements de la description de service.  
  
- Extension du fichier de configuration  
  
 Cet exemple utilise un attribut personnalisé. Lorsque <xref:System.ServiceModel.ServiceHost> est construit, il examine les attributs utilisés dans la définition de type du service et ajoute les comportements disponibles à la collection de comportements de la description de service.  
  
 L'interface <xref:System.ServiceModel.Description.IServiceBehavior> a trois méthode : <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> et <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. La méthode <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> permet de s'assurer que le comportement peut être appliqué au service. Dans cet exemple, l'implémentation garantit que le service n'est pas configuré avec <xref:System.ServiceModel.InstanceContextMode.Single>. La méthode <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> permet de configurer les liaisons du service. Elle n'est pas requise dans ce scénario. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> permet de configurer les répartiteurs du service. Cette méthode est appelée par WCF lorsque le <xref:System.ServiceModel.ServiceHost> est en cours d’initialisation. Les paramètres suivants sont passés dans cette méthode :  
  
- `Description` : cet argument fournit la description de service pour l'ensemble du service. Il permet d’inspecter les données de description sur les points de terminaison, les contrats, les liaisons et autres données du service.  
  
- `ServiceHostBase`  cet argument fournit le <xref:System.ServiceModel.ServiceHostBase> actuellement initialisé.  
  
 Dans l'implémentation <xref:System.ServiceModel.Description.IServiceBehavior> personnalisée, une nouvelle instance de `ObjectPoolingInstanceProvider` est instanciée et assignée à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> dans chaque <xref:System.ServiceModel.Dispatcher.DispatchRuntime> de ServiceHostBase.  
  
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
  
 Outre une implémentation <xref:System.ServiceModel.Description.IServiceBehavior>, la classe <xref:System.EnterpriseServices.ObjectPoolingAttribute> a plusieurs membres pour personnaliser le mise en pool d’objets à l’aide des arguments d’attribut. Ces membres incluent <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> et <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, pour faire correspondre le jeu de fonctionnalités de mise en pool d’objets fourni par .NET Enterprise Services.  
  
 Le comportement de mise en pool d’objets peut maintenant être ajouté à un service WCF en annotant l’implémentation de service avec l’attribut personnalisé nouvellement créé `ObjectPooling` .  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Exécution de l'exemple  

 L'exemple montre les avantages qui peuvent être retirés en termes de performance en utilisant le mise en pool d’objets dans des scénarios spécifiques.  
  
 L'application de service implémente deux services : `WorkService` et `ObjectPooledWorkService`. Ces deux services partagent la même implémentation : ils requièrent tous deux une initialisation gourmande en ressources, puis exposent une méthode `DoWork()` qui s'avère relativement peu gourmande. La seule différence est que le mise en pool d’objets de `ObjectPooledWorkService` est configuré :  
  
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
  
 Lorsque vous exécutez le client, il chronomètre l'appel à `WorkService` 5 fois. Il chronomètre ensuite l'appel à `ObjectPooledWorkService` 5 fois. La différence de temps est ensuite affichée :  
  
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
> La première fois que le client est exécuté, les deux services semblent prendre environ le même temps. Si vous ré-exécutez l'exemple, vous constatez que `ObjectPooledWorkService` retourne beaucoup plus rapidement car une instance de cet objet existe déjà dans le pool.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!NOTE]
> Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
