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
# <a name="instancing-initialization"></a>Instancing Initialization
Cet exemple étend l’exemple de [regroupement](pooling.md) en définissant une interface, `IObjectControl` , qui personnalise l’initialisation d’un objet en l’activant et en le désactivant. Le client appelle des méthodes qui retournent l'objet au pool et d'autres qui ne retournent pas l'objet au pool.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="extensibility-points"></a>Points d'extensibilité  
 La première étape de la création d’une extension Windows Communication Foundation (WCF) consiste à décider du point d’extensibilité à utiliser. Dans WCF, le terme *EndpointDispatcher* fait référence à un composant Runtime chargé de convertir des messages entrants en appels de méthode sur le service de l’utilisateur et de convertir les valeurs de retour de cette méthode en message sortant. Un service WCF crée un EndpointDispatcher pour chaque point de terminaison.  
  
 L'EndpointDispatcher permet l'extensibilité de l'étendue du point de terminaison (pour tous les messages reçus ou envoyés par le service) à l'aide de la classe <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. Cette classe vous permet de personnaliser différentes propriétés qui contrôlent le comportement de l'EndpointDispatcher. Cet exemple se concentre sur la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> qui pointe sur l'objet qui fournit les instances de la classe de service.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 Dans WCF, EndpointDispatcher crée des instances d’une classe de service à l’aide d’un fournisseur d’instances qui implémente l' <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface. Cette interface possède uniquement deux méthodes :  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> : lorsqu'un message arrive, le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> afin de créer une instance de la classe de service pour traiter le message. La fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Par exemple, si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, une nouvelle instance de la classe de service est créée pour traiter chaque message qui arrive, et <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> est donc appelée chaque fois qu'un message arrive.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> : lorsque l'instance de service finit de traiter le message, l'EndpointDispatcher appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>. À l'instar de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, la fréquence des appels à cette méthode est déterminée par la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Mise en pool d’objets  
 La classe `ObjectPoolInstanceProvider` contient l'implémentation pour le mise en pool d’objets. Cette classe implémente l'interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pour interagir avec la couche de modèle de service. Lorsque l'EndpointDispatcher appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, au lieu de créer une instance, l'implémentation personnalisée recherche un objet existant dans un pool en mémoire. Si aucun n'est disponible, il est retourné. Sinon, `ObjectPoolInstanceProvider` vérifie si la propriété `ActiveObjectsCount` (nombre d'objets retournés depuis le pool) a atteint la taille de pool maximale. Si ce n'est pas le cas, une nouvelle instance est créée et retournée à l'appelant et `ActiveObjectsCount` est incrémenté par la suite. Sinon, une demande de création d'objet est mise en file d'attente pendant le laps de temps configuré. L'implémentation pour `GetObjectFromThePool` est présentée dans l'exemple de code suivant.  
  
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
  
 L'implémentation `ReleaseInstance` personnalisée ajoute de nouveau l'instance libérée au pool et décrémente la valeur `ActiveObjectsCount`. L’EndpointDispatcher peut appeler ces méthodes à partir de différents threads et, par conséquent, l’accès synchronisé aux membres au niveau de la classe dans la classe `ObjectPoolInstanceProvider` est requis.  
  
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
  
 La `ReleaseInstance` méthode fournit une fonctionnalité *d’initialisation de nettoyage* . Normalement, le pool gère un nombre minimal d'objets pendant sa durée de vie. Toutefois, il peut y avoir des périodes d'utilisation excessive qui requièrent la création d'objets supplémentaires dans le pool afin d'atteindre la limite maximale spécifiée dans la configuration. Par la suite, lorsque le pool devient moins actif, ces objets en surplus peuvent devenir une surcharge supplémentaire. Par conséquent, lorsque le `activeObjectsCount` atteint zéro, une minuterie d'inactivité est démarrée, qui déclenche et effectue un cycle de nettoyage.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 Les extensions de couche ServiceModel sont raccordées à l’aide des comportements suivants :  
  
- Comportements de service : permettent de personnaliser l'ensemble de l'exécution du service.  
  
- Comportements de point de terminaison : permettent de personnaliser un point de terminaison de service particulier, y compris l'EndpointDispatcher.  
  
- Comportements de contrat : permettent de personnaliser la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> ou la classe <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sur le client ou le service respectivement.  
  
- Comportements d'opération : permettent de personnaliser la classe <xref:System.ServiceModel.Dispatcher.ClientOperation> ou la classe <xref:System.ServiceModel.Dispatcher.DispatchOperation> sur le client ou le service respectivement.  
  
 Dans le cadre d’une extension de mise en pool d’objets, il est possible de créer un comportement de point de terminaison ou un comportement de service. Dans cet exemple, nous utilisons un comportement de service qui applique la capacité de mise en mise en pool d’objets à chaque point de terminaison du service. Pour ce faire, implémentez l'interface <xref:System.ServiceModel.Description.IServiceBehavior>. Il existe plusieurs méthodes pour que le ServiceModel tienne compte des comportements personnalisés :  
  
- Utilisation d'un attribut personnalisé.  
  
- L'ajouter de façon impérative à la collection de comportements de la description de service.  
  
- Extension du fichier de configuration  
  
 Cet exemple utilise un attribut personnalisé. Lorsque <xref:System.ServiceModel.ServiceHost> est généré, il examine les attributs utilisés dans la définition de type du service et ajoute les comportements disponibles à la collection de comportements de la description de service.  
  
 L' <xref:System.ServiceModel.Description.IServiceBehavior> interface a trois méthodes : <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` et <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> . Ces méthodes sont appelées par WCF lorsque le <xref:System.ServiceModel.ServiceHost> est en cours d’initialisation. l'<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> est appelée en premier ; elle autorise l'inspection du service pour retrouver les éventuelles incohérences. l'<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> est appelée ensuite ; cette méthode est requise uniquement dans les scénarios très avancés. l'<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> est appelée en dernier ; elle est responsable de la configuration de l'exécution. Les paramètres suivants sont passés dans <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :  
  
- `Description` : ce paramètre fournit la description de service pour le service entier. Il permet d’inspecter les données de description des points de terminaison, des contrats et des liaisons, et les autres données associées au service.  
  
- `ServiceHostBase` : ce paramètre fournit le <xref:System.ServiceModel.ServiceHostBase> en cours d'initialisation.  
  
 Dans l'implémentation <xref:System.ServiceModel.Description.IServiceBehavior> personnalisée, une nouvelle instance du `ObjectPoolInstanceProvider` est instanciée et assignée à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> dans chaque <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> joint au <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Outre une implémentation <xref:System.ServiceModel.Description.IServiceBehavior>, la classe `ObjectPoolingAttribute` a plusieurs membres pour personnaliser le mise en pool d’objets à l’aide des arguments d’attribut. Ces membres incluent `MaxSize`, `MinSize`, `Enabled` et `CreationTimeout`, pour faire correspondre le jeu de fonctionnalités de mise en mise en pool d’objets fourni par .NET Enterprise Services.  
  
 Le comportement de mise en pool d’objets peut maintenant être ajouté à un service WCF en annotant l’implémentation de service avec l’attribut personnalisé nouvellement créé `ObjectPooling` .  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Activation et désactivation du raccordement  
 L'objectif principal de la mise en mise en pool d’objets est d'optimiser la création et l'initialisation relativement coûteuses des objets éphémères. Par conséquent, elle peut singulièrement améliorer les performances d'une application si elle est utilisée correctement. Étant donné que l'objet est retourné depuis le pool, le constructeur est appelé une seule fois. Toutefois, certaines applications requièrent un certain niveau de contrôle afin de pouvoir initialiser et nettoyer les ressources utilisées dans un contexte unique. Par exemple, un objet utilisé pour un ensemble de calculs peut réinitialiser ses champs privés avant de traiter le calcul suivant. Les Enterprise Services ont activé ce type d'initialisation spécifique au contexte en laissant le développeur d'objets substituer les méthodes `Activate` et `Deactivate` de la classe <xref:System.EnterpriseServices.ServicedComponent> de base.  
  
 Le pool d'objets appelle la méthode `Activate` juste avant de retourner l'objet depuis le pool. `Deactivate` est appelé lorsque l'objet est retourné au pool. La classe <xref:System.EnterpriseServices.ServicedComponent> de base a également une propriété `boolean` appelée `CanBePooled`, qui peut être utilisée pour notifier au pool que l'objet peut être davantage regroupé.  
  
 Pour reproduire ces fonctionnalités, l'exemple déclare une interface publique (`IObjectControl`) avec les membres susmentionnés. Puis cette interface est implémentée par les classes de service conçues pour assurer l'initialisation spécifique au contexte. L’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceProvider> doit être modifiée pour satisfaire ces exigences. À présent, chaque fois que vous récupérez un objet en appelant la `GetInstance` méthode, vous devez vérifier si l’objet implémente `IObjectControl.` , si c’est le cas, vous devez appeler la `Activate` méthode de manière appropriée.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Lors du retour d'un objet au pool, un contrôle de la propriété `CanBePooled` est requis avant d'ajouter de nouveau l'objet au pool.  
  
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
  
 Vu que le développeur de service peut décider si un objet peut être regroupé ou non, le nombre d'objets dans le pool à un moment donné peut être inférieur à la taille minimale. Par conséquent, vous devez vérifier si le nombre d'objets est inférieur au minimum et effectuer l'initialisation nécessaire dans la procédure de nettoyage.  
  
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
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur Enter dans chaque fenêtre de console pour arrêter le service et le client.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
