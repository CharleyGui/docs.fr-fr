---
title: Durable Instance Context
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 567ca62d48e80993328548b11f8b59c4fcd355fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600592"
---
# <a name="durable-instance-context"></a>Durable Instance Context

Cet exemple montre comment personnaliser le runtime Windows Communication Foundation (WCF) pour activer des contextes d’instance durables. Il utilise SQL Server 2005 comme magasin de sauvegarde (SQL Server 2005 Express dans ce cas précis). Toutefois, il permet également d'accéder aux mécanismes de stockage personnalisés.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Cet exemple implique l’extension de la couche de canal et de la couche de modèle de service de WCF. Par conséquent, il est nécessaire de comprendre les concepts sous-jacents avant d'aborder les détails de l'implémentation.

Les contextes d'instance fiables se trouvent souvent dans des scénarios réels. Une application de panier d’achat, par exemple, a la possibilité de suspendre des achats à mi-chemin et de la poursuivre un autre jour. De cette façon, lorsque nous visitons le panier d'achat le jour suivant, le contexte d'origine est restauré. Il est important de noter que l'application de panier d'achat (sur le serveur) ne conserve pas l'instance correspondante en cas de déconnexion. À la place, elle rend son état persistant dans un média de stockage fiable et l'utilise lors de la construction d'une nouvelle instance pour le contexte restauré. Par conséquent l'instance de service qui peut servir pour le même contexte n'est pas la même que l'instance précédente (autrement dit, elle n'a pas la même adresse mémoire).

Le contexte d'instance fiable est rendu possible par un petit protocole qui échange un ID de contexte entre le client et le service. Cet ID de contexte est créé sur le client et est transmis au service. Lorsque l'instance de service est créée, l'exécution du service essaie de charger l'état persistant qui correspond à cet ID de contexte à partir d'un stockage persistant (par défaut, il s'agit d'une base de données SQL Server 2005). Si aucun État n’est disponible, la nouvelle instance a son état par défaut. L'implémentation de service utilise un attribut personnalisé pour marquer les opérations qui modifient l'état de l'implémentation de service afin que l'exécution puisse enregistrer l'instance de service après les avoir appelées.

Dans la description précédente, on distingue clairement deux étapes permettant d'atteindre cet objectif :

1. Modification du message sur le câble afin de transmettre l'ID de contexte.

2. Modification du comportement local du service afin d'implémenter la logique d'instanciation personnalisée.

Étant donné que la première dans la liste affecte les messages sur le câble, elle doit être implémentée en tant que canal personnalisé et être raccordée à la couche de canal. La dernière affecte uniquement le comportement local du service et peut par conséquent être implémentée en étendant plusieurs points d'extensibilité. Chacune des extensions suivantes est traitée dans les sections ci-après.

## <a name="durable-instancecontext-channel"></a>Canal InstanceContext fiable

La première chose à examiner est une extension de la couche de canal. La première étape de l'écriture d'un canal personnalisé consiste à déterminer la structure de communication du canal. Lorsqu’un nouveau protocole câble est introduit, le canal doit fonctionner avec presque n’importe quel autre canal dans la pile de canaux. Par conséquent, il doit prendre en charge l’ensemble des modèles d’échange de messages. Toutefois, la fonctionnalité principale du canal est la même, quelle que soit sa structure de communication. Plus précisément, du côté client il doit écrire l'ID de contexte dans les messages, et du côté service il doit lire cet ID de contexte à partir des messages et le passer aux niveaux supérieurs. De ce fait, une classe `DurableInstanceContextChannelBase` est créée et agit en tant que classe de base abstraite pour toutes les implémentations de canal de contexte d'instance fiable. Cette classe contient les fonctions de gestion de machine d'état courantes ainsi que deux membres protégés afin d'appliquer et de lire les informations de contexte vers et à partir des messages.

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

Ces deux méthodes utilisent des implémentations `IContextManager` pour écrire et lire l'ID de contexte vers ou à partir du message  ( `IContextManager` est une interface personnalisée utilisée pour définir le contrat pour tous les gestionnaires de contexte.) Le canal peut inclure l’ID de contexte dans un en-tête SOAP personnalisé ou dans un en-tête de cookie HTTP. Chaque implémentation de gestionnaire de contexte hérite de la classe `ContextManagerBase` qui contient les fonctionnalités communes de tous les gestionnaires de contexte. La méthode `GetContextId` de cette classe permet de générer l'ID de contexte à partir du client. Lorsqu'un ID de contexte est généré pour la première fois, cette méthode l'enregistre dans un fichier texte dont le nom est construit par l'adresse du point de terminaison distant (les caractères de nom de fichier non valides dans les URI classiques sont remplacés par des caractères @).

Par la suite, lorsque l'ID de contexte est requis pour le même point de terminaison distant, il vérifie si un fichier approprié existe. Si c'est le cas, il lit l'ID de contexte et retourne. Sinon, il retourne un ID de contexte généré récemment et l'enregistre dans un fichier. Avec la configuration par défaut, ces fichiers sont placés dans un répertoire appelé ContextStore, qui réside dans le répertoire Temp de l’utilisateur actuel. Toutefois, cet emplacement est configurable à l’aide de l’élément de liaison.

Le mécanisme utilisé pour transporter l'ID de contexte est configurable. Il peut être écrit dans l'en-tête cookie HTTP ou dans un en-tête SOAP personnalisé. L'approche utilisant l'en-tête SOAP personnalisé permet d'utiliser ce protocole avec des protocoles non HTTP (par exemple, TCP ou canaux nommés). Les deux classes `MessageHeaderContextManager` et `HttpCookieContextManager` implémentent ces deux options.

Elles écrivent l'ID de contexte dans le message de manière appropriée. Par exemple, la classe `MessageHeaderContextManager` l'écrit dans un en-tête SOAP de la méthode `WriteContext`.

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

Les méthodes `ApplyContext` et `ReadContextId` de la classe `DurableInstanceContextChannelBase` appellent `IContextManager.ReadContext` et `IContextManager.WriteContext`, respectivement. Toutefois, ces gestionnaires de contexte ne sont pas directement créés par la classe `DurableInstanceContextChannelBase`. Cette tâche est accomplie par la classe `ContextManagerFactory`.

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

La méthode `ApplyContext` est appelée par les canaux d'envoi. Elle injecte l'ID de contexte dans les messages sortants. La méthode `ReadContextId` est appelée par les canaux de réception. Cette méthode garantit que l’ID de contexte est disponible dans les messages entrants et l’ajoute à la collection `Properties` de la classe `Message`. Elle lève également une exception `CommunicationException` en cas d'échec de lecture de l'ID de contexte et provoque donc l'abandon du canal.

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

Avant de poursuivre, il est important de comprendre l’utilisation de la collection `Properties` dans la classe `Message`. En général, cette collection `Properties` est utilisée lors du passage des données des niveaux inférieurs aux niveaux supérieurs de la couche de canal. De cette manière, les données souhaitées peuvent être fournies aux niveaux supérieurs de façon cohérente, quels que soient les détails du protocole. En d’autres termes, la couche de canal peut envoyer et recevoir l’ID de contexte comme un en-tête SOAP ou un en-tête de cookie HTTP. Mais il n’est pas nécessaire que les niveaux supérieurs connaissent ces détails car la couche de canal rend ces informations disponibles dans la collection `Properties`.

La classe `DurableInstanceContextChannelBase` étant maintenant en place, l'ensemble des dix interfaces nécessaires (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) doivent être implémentées. Elles ressemblent à chaque modèle d’échange de messages disponible (datagramme, simplex, duplex et leurs variantes de session). Chacune de ces implémentations hérite de la classe de base décrite précédemment et appelle `ApplyContext` et de `ReadContextId` manière appropriée. Par exemple, `DurableInstanceContextOutputChannel`, qui implémente l'interface IOutputChannel, appelle la méthode `ApplyContext` de chaque méthode qui envoie les messages.

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

En revanche,, `DurableInstanceContextInputChannel` qui implémente l’interface, `IInputChannel` appelle la `ReadContextId` méthode dans chaque méthode, qui reçoit les messages.

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

En outre, ces implémentations de canal délèguent les appels de méthode au canal inférieur dans la pile de canaux. Toutefois, les variantes de session ont une logique de base permettant de s'assurer que l'ID de contexte est envoyé et est lu uniquement pour le premier message qui provoque la création de la session.

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

Ces implémentations de canal sont ensuite ajoutées au runtime du canal WCF par la `DurableInstanceContextBindingElement` classe et la `DurableInstanceContextBindingElementSection` classe de manière appropriée. Consultez la documentation de l’exemple de canal [HttpCookieSession](httpcookiesession.md) pour plus d’informations sur les éléments de liaison et les sections d’éléments de liaison.

## <a name="service-model-layer-extensions"></a>Extensions de la couche de modèle de service

Maintenant que l'ID de contexte a traversé la couche de canal, le comportement de service peut être implémenté afin de personnaliser l'instanciation. Dans cet exemple, un gestionnaire de stockage est utilisé pour charger et enregistrer l'état à partir de ou vers le magasin persistant. Comme expliqué précédemment, cet exemple fournit un gestionnaire de stockage qui utilise le SQL Server 2005 comme magasin de sauvegarde. Toutefois, il est également possible d’ajouter des mécanismes de stockage personnalisés à cette extension. Pour ce faire, une interface publique est déclarée et doit être implémentée par tous les gestionnaires de stockage.

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

La classe `SqlServerStorageManager` contient l'implémentation `IStorageManager` par défaut. Dans sa `SaveInstance` méthode, l’objet donné est sérialisé à l’aide du XmlSerializer et est enregistré dans la base de données SQL Server.

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

Dans la `GetInstance` méthode, les données sérialisées sont lues pour un ID de contexte donné et l’objet construit à partir de celle-ci est retourné à l’appelant.

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

Les utilisateurs de ces gestionnaires de stockage ne sont pas supposés les instancier directement. Ils utilisent la classe `StorageManagerFactory`, qui abstrait à partir des détails de création de gestionnaire de stockage. Cette classe possède le membre statique `GetStorageManager` qui crée une instance d'un type de gestionnaire de stockage donné. Si le paramètre de type est `null`, cette méthode crée une instance de la classe `SqlServerStorageManager` par défaut et la retourne. Elle valide également le type donné afin de s'assurer qu'il implémente l'interface `IStorageManager`.

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

L'infrastructure nécessaire pour lire et écrire des instances à partir du stockage persistant est implémentée. Les étapes nécessaires pour modifier le comportement de service doivent maintenant être effectuées.

La première étape de ce processus consiste à enregistrer l'ID de contexte, qui a traversé la couche de canal jusqu'au InstanceContext actuel. InstanceContext est un composant d’exécution qui agit comme lien entre le répartiteur WCF et l’instance de service. Il permet de fournir un comportement et un état supplémentaires à l'instance de service. Cet aspect est essentiel car dans la communication de session, l'ID de contexte est envoyé uniquement avec le premier message.

WCF permet d’étendre son composant d’exécution InstanceContext en ajoutant un nouvel État et un nouveau comportement à l’aide de son modèle d’objet extensible. Le modèle d’objet extensible est utilisé dans WCF pour étendre des classes d’exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d’État à un objet. Il existe trois interfaces dans le modèle d’objet extensible-IExtensibleObject \<T> , IExtension \<T> et IExtensionCollection \<T> :

- L' \<T> interface IExtensibleObject est implémentée par des objets qui autorisent les extensions qui personnalisent leurs fonctionnalités.

- L' \<T> interface IExtension est implémentée par des objets qui sont des extensions de classes de type T.

- L' \<T> interface IExtensionCollection est une collection de IExtensions qui permet de récupérer des IExtensions par leur type.

Par conséquent, vous devez créer une classe InstanceContextExtension qui implémente l'interface IExtension et définit l'état requis pour enregistrer l'ID de contexte. Cette classe fournit également l'état permettant de conserver le gestionnaire de stockage utilisé. Une fois que le nouvel état est enregistré, il ne doit pas être possible de le modifier. L'état est donc fourni et enregistré dans l'instance au moment de sa construction et n'est ensuite accessible qu'en lecture seule.

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

La classe InstanceContextInitializer implémente l'interface IInstanceContextInitializer et ajoute l'extension de contexte d'instance à la collection Extensions du InstanceContext en cours de construction.

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

Comme décrit précédemment, l'ID de contexte est lu à partir de la collection `Properties` de la classe `Message`, puis il est passé au constructeur de la classe d'extension. Cette étape montre comment les informations peuvent être échangées entre les couches de façon cohérente.

L'étape importante suivante consiste à substituer le processus de création d'instance de service. WCF permet d’implémenter des comportements d’instanciation personnalisés et de les raccorder au runtime à l’aide de l’interface IInstanceProvider. Pour ce faire, la nouvelle classe `InstanceProvider` est implémentée. Le type de service attendu à partir du fournisseur d’instance est accepté dans le constructeur. Il est par la suite utilisé pour créer des instances. Dans l' `GetInstance` implémentation, une instance d’un gestionnaire de stockage est créée à la recherche d’une instance persistante. Si elle retourne `null` , une nouvelle instance du type de service est instanciée et retournée à l’appelant.

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

L’étape importante suivante consiste à installer les `InstanceContextExtension` `InstanceContextInitializer` classes, et `InstanceProvider` dans le runtime du modèle de service. Un attribut personnalisé peut être utilisé pour marquer les classes d'implémentation de service afin d'installer le comportement. `DurableInstanceContextAttribute` contient l'implémentation pour cet attribut et implémente l'interface `IServiceBehavior` afin d'étendre l'ensemble de l'exécution du service.

Cette classe possède une propriété qui accepte le type du gestionnaire de stockage à utiliser. De cette façon, l’implémentation permet aux utilisateurs de spécifier leur propre `IStorageManager` implémentation en tant que paramètre de cet attribut.

Dans l' `ApplyDispatchBehavior` implémentation, le `InstanceContextMode` de l' `ServiceBehavior` attribut actuel est en cours de vérification. Si cette propriété a pour valeur Singleton, l'activation de l'instanciation fiable n'est pas possible et une exception `InvalidOperationException` est levée pour notifier l'hôte.

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

Puis les instances du gestionnaire de stockage, l'initialiseur de contexte d'instance et le fournisseur d'instances sont créés et installés dans le `DispatchRuntime` créé pour chaque point de terminaison.

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

En résumé des étapes effectuées jusqu'à présent, cet exemple a produit un canal qui a activé le protocole de câble personnalisé pour l'échange d'ID de contexte personnalisé et il remplace également le comportement d'instanciation par défaut afin de charger les instances à partir du stockage persistant.

Il reste donc à enregistrer l'instance de service dans le stockage persistant. Comme indiqué précédemment, les fonctionnalités requises pour enregistrer l'état dans une implémentation `IStorageManager` existent déjà. Nous devons maintenant intégrer ce avec le runtime WCF. Un autre attribut est requis et est applicable aux méthodes de la classe d'implémentation de service. Cet attribut est supposé s'appliquer aux méthodes qui modifient l'état de l'instance de service.

La classe `SaveStateAttribute` implémente ces fonctionnalités. Il implémente également `IOperationBehavior` la classe pour modifier le runtime WCF pour chaque opération. Quand une méthode est marquée avec cet attribut, le runtime WCF appelle la `ApplyBehavior` méthode pendant la construction de la appropriée `DispatchOperation` . Cette implémentation de méthode comporte une seule ligne de code :

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

Cette instruction crée une instance de type `OperationInvoker` et l'assigne à la propriété `Invoker` du `DispatchOperation` en cours de construction. La classe `OperationInvoker` est un wrapper pour le demandeur d'opération par défaut créé pour `DispatchOperation`. Cette classe implémente l’interface `IOperationInvoker`. Dans l' `Invoke` implémentation de méthode, l’appel de méthode réel est délégué au demandeur d’opération interne. Toutefois, avant de retourner les résultats, le gestionnaire de stockage du `InstanceContext` est utilisé pour enregistrer l'instance de service.

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a>Utilisation de l'extension

La couche de canal et les extensions de couche de modèle de service sont toutes deux effectuées et peuvent désormais être utilisées dans les applications WCF. Les services doivent ajouter le canal dans la pile de canaux à l’aide d’une liaison personnalisée, puis marquer les classes d’implémentation de service avec les attributs appropriés.

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

Les applications clientes doivent ajouter DurableInstanceContextChannel dans la pile de canaux à l’aide d’une liaison personnalisée. Pour configurer le canal de façon déclarative dans le fichier de configuration, la section d'élément de liaison doit être ajoutée à la collection d'extensions d'élément de liaison.

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

L’élément de liaison peut maintenant être utilisé avec une liaison personnalisée à l’instar des autres éléments de liaison standard :

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a>Conclusion

Cet exemple a montré comment créer un canal de protocole personnalisé et comment personnaliser le comportement de service permettant de l'activer.

L’extension peut encore être améliorée en permettant aux utilisateurs de spécifier l’implémentation `IStorageManager` à l’aide d’une section de configuration. Cela permet de modifier le magasin de sauvegarde sans avoir à recompiler le code de service.

En outre, vous pouvez essayer d'implémenter une classe (par exemple, `StateBag`) qui encapsule l'état de l'instance. Cette classe est chargée de rendre l'état persistant chaque fois qu'il change. De cette manière, vous pouvez éviter d'utiliser l'attribut `SaveState` et travailler de manière plus précise (par exemple, vous pouvez rendre l'état persistant lorsqu'il est réellement modifié plutôt que de l'enregistrer chaque fois qu'une méthode avec l'attribut `SaveState` est appelée).

Lorsque vous exécutez l'exemple, la sortie suivante s'affiche. Le client ajoute deux éléments à son panier d'achat puis place la liste d'éléments dans celui-ci à partir du service. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> La reconstruction du service remplace le fichier de base de données. Pour observer l'état conservé sur plusieurs exécutions de l'exemple, ne reconstruisez pas l'exemple d'une exécution à l'autre.

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!NOTE]
> Vous devez exécuter SQL Server 2005 ou SQL Express 2005 pour exécuter cet exemple. Si vous exécutez SQL Server 2005, vous devez modifier la configuration de la chaîne de connexion du service. Lors de l'exécution sur plusieurs ordinateurs, SQL Server est uniquement requis sur l'ordinateur serveur.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
