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
# <a name="custom-lifetime"></a>Durée de vie personnalisée

Cet exemple montre comment écrire une extension Windows Communication Foundation (WCF) pour fournir des services de durée de vie personnalisés pour les instances de service WCF partagées.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.

## <a name="shared-instancing"></a>Instanciation partagée

WCF offre plusieurs modes d’instanciation pour vos instances de service. Le mode d’instanciation partagé abordé dans cet article fournit un moyen de partager une instance de service entre plusieurs canaux. Les clients peuvent contacter une méthode de fabrique dans le service et créer un nouveau canal pour démarrer la communication. L’extrait de code suivant montre comment une application cliente crée un canal vers une instance de service existante :

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

Contrairement aux autres modes d'instanciation, l'instanciation partagée a une façon unique de libérer des instances de service. Par défaut, lorsque tous les canaux sont fermés pour une <xref:System.ServiceModel.InstanceContext>, le runtime du service WCF vérifie si le service <xref:System.ServiceModel.InstanceContextMode> est configuré pour <xref:System.ServiceModel.InstanceContextMode.PerCall> ou <xref:System.ServiceModel.InstanceContextMode.PerSession>, et si c’est le cas, libère l’instance et réclame les ressources. Si un <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> personnalisé est utilisé, WCF appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de l’implémentation du fournisseur avant de libérer l’instance. Si <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> retourne `true` l’instance est libérée, dans le cas contraire, l’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est chargée de notifier la `Dispatcher` de l’état inactif à l’aide d’une méthode de rappel. Pour ce faire, appelez la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> du fournisseur.

Cet exemple montre comment vous pouvez différer la libération du <xref:System.ServiceModel.InstanceContext> avec un délai d’inactivité de 20 secondes.

## <a name="extending-the-instancecontext"></a>Extension de l'InstanceContext

Dans WCF, <xref:System.ServiceModel.InstanceContext> est le lien entre l’instance de service et le `Dispatcher`. WCF vous permet d’étendre ce composant d’exécution en ajoutant un nouvel État ou comportement à l’aide de son modèle d’objet extensible. Le modèle d’objet extensible est utilisé dans WCF pour étendre des classes d’exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d’État à un objet. Le modèle d'objet extensible contient trois interfaces : <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601> et <xref:System.ServiceModel.IExtensionCollection%601>.

L’interface <xref:System.ServiceModel.IExtensibleObject%601> est implémentée par des objets pour autoriser des extensions qui personnalisent leurs fonctionnalités.

L’interface <xref:System.ServiceModel.IExtension%601> est implémentée par des objets qui peuvent être des extensions de classes de type `T`.

Enfin, l’interface <xref:System.ServiceModel.IExtensionCollection%601> est une collection d’implémentations de <xref:System.ServiceModel.IExtension%601> qui permet de récupérer une implémentation de <xref:System.ServiceModel.IExtension%601> par leur type.

Par conséquent, pour étendre le <xref:System.ServiceModel.InstanceContext>, vous devez implémenter l’interface <xref:System.ServiceModel.IExtension%601>. Dans cet exemple de projet, la classe `CustomLeaseExtension` contient cette implémentation.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

L'interface <xref:System.ServiceModel.IExtension%601> possède deux méthodes : <xref:System.ServiceModel.IExtension%601.Attach%2A> et <xref:System.ServiceModel.IExtension%601.Detach%2A>. Comme leur nom le laisse supposer, ces deux méthodes sont appelées lorsque le runtime attache l’extension à une instance de la classe <xref:System.ServiceModel.InstanceContext> et l’en détache. Dans cet exemple, la méthode `Attach` est utilisée pour effectuer le suivi de l’objet <xref:System.ServiceModel.InstanceContext> qui appartient à l’instance actuelle de l’extension.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

En outre, vous devez ajouter l’implémentation dont l’extension a besoin pour fournir la prise en charge de la durée de vie étendue. Par conséquent, l’interface `ICustomLease` est déclarée avec les méthodes souhaitées et est implémentée dans la classe `CustomLeaseExtension`.

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

Lorsque WCF appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> dans l’implémentation <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, cet appel est routé vers la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de l' `CustomLeaseExtension`. Ensuite, le `CustomLeaseExtension` vérifie son état privé pour déterminer si le <xref:System.ServiceModel.InstanceContext> est inactif. S’il est inactif, il retourne `true`. Sinon, elle démarre un minuteur pour l'extension spécifiée de la durée de vie.

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

Dans l’événement `Elapsed` de la minuterie, la fonction de rappel dans le répartiteur est appelée afin de démarrer un autre cycle de nettoyage.

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

Il n’existe aucun moyen de renouveler le minuteur en cours d’exécution lorsqu’un nouveau message arrive pour l’instance déplacée vers l’état inactif.

L'exemple implémente <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> pour intercepter les appels à la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> et les router vers `CustomLeaseExtension`. L'implémentation d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est contenue dans la classe `CustomLifetimeLease`. La méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> est appelée lorsque WCF est sur le paragraphe de libérer l’instance de service. Toutefois, il n'existe qu'une instance d'une implémentation d'`ISharedSessionInstance` particulière dans la collection <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> du ServiceBehavior. Cela signifie qu’il n’existe aucun moyen de savoir si la <xref:System.ServiceModel.InstanceContext> est fermée au moment où WCF vérifie la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. Par conséquent, cet exemple utilise le verrouillage de thread pour sérialiser les requêtes vers la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.

> [!IMPORTANT]
> Le recours au verrouillage de threads n'est pas une approche recommandée, car la sérialisation peut considérablement affecter les performances de votre application.

Un champ de membre privé est utilisé dans la classe `CustomLifetimeLease` pour suivre l’état inactif et est retourné par la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. Chaque fois que la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> est appelée, le champ `isIdle` est retourné et réinitialisé à `false`.  L'affectation de `false` à cette valeur est indispensable pour que le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.

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

Si la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> retourne `false`, le répartiteur inscrit une fonction de rappel à l’aide de la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>. Cette méthode reçoit une référence à l’<xref:System.ServiceModel.InstanceContext> libéré. Par conséquent, l’exemple de code peut interroger l’extension de type `ICustomLease` et vérifier la propriété `ICustomLease.IsIdle` dans l’état étendu.

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

Avant que la propriété `ICustomLease.IsIdle` soit activée, la propriété callback doit être définie comme ceci est essentiel pour que `CustomLeaseExtension` notifie le répartiteur lorsqu’il devient inactif. Si `ICustomLease.IsIdle` retourne `true`, le membre privé `isIdle` reçoit simplement dans `CustomLifetimeLease` la valeur `true` et appelle la méthode de rappel. Étant donné que le code contient un verrou, les autres threads ne peuvent pas modifier la valeur de ce membre privé. Et la prochaine fois que le répartiteur appelle la <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, il retourne `true` et autorise le répartiteur à libérer l’instance.

Le travail préparatoire étant à présent terminé, l’extension personnalisée doit être raccordée au modèle de service. Pour raccorder l’implémentation de `CustomLeaseExtension` au <xref:System.ServiceModel.InstanceContext>, WCF fournit l’interface <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> pour effectuer l’amorçage de <xref:System.ServiceModel.InstanceContext>. Dans l’exemple, la classe `CustomLeaseInitializer` implémente cette interface et ajoute une instance de `CustomLeaseExtension` à la collection <xref:System.ServiceModel.InstanceContext.Extensions%2A> à partir de la seule initialisation de la méthode. Cette méthode est appelée par le répartiteur en initialisant l'<xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Enfin, l’implémentation de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est raccordée au modèle de service à l’aide de l’implémentation de <xref:System.ServiceModel.Description.IServiceBehavior>. Cette implémentation est placée dans la classe `CustomLeaseTimeAttribute` et dérive également de la classe de base <xref:System.Attribute> pour exposer ce comportement en tant qu'attribut.

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

Ce comportement peut être ajouté à une classe de l'exemple de service en l'annotant avec l'attribut `CustomLeaseTime`.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
