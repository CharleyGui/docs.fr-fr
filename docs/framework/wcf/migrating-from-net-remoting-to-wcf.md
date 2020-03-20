---
title: Migration de .NET Remoting vers WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183960"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migration de .NET Remoting vers WCF
Cet article décrit comment migrer une application .NET Remoting vers Windows Communication Foundation (WCF). Il compare d'abord les concepts similaires entre ces deux produits, puis explique comment transposer plusieurs scénarios Remoting courants dans WCF.  
  
 .NET Remoting est un produit hérité qui est uniquement pris en charge à des fins de compatibilité descendante. Il n'est pas sécurisé dans les environnements de confiance mixte en raison de son incapacité à préserver les niveaux de confiance distincts entre le client et le serveur. Par exemple, vous ne devez jamais exposer un point de terminaison .NET Remoting à Internet ou à des clients non approuvés. Nous vous recommandons de migrer les applications Remoting existantes vers des technologies plus récentes qui offrent davantage de sécurité. Si l'application utilise uniquement le protocole HTTP et qu'elle repose sur une conception RESTful, nous recommandons l'API Web ASP.NET. Pour plus d'informations, consultez l'API Web ASP.NET. Si l'application est basée sur SOAP ou qu'elle nécessite des protocoles non-HTTP (comme TCP), nous recommandons WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Comparaison de .NET Remoting à WCF  
 Cette section compare les blocs de construction de base de .NET Remoting à leurs équivalents WCF. Nous utiliserons ces éléments de base plus tard pour créer des scénarios communs client-serveur dans WCF. Le graphique suivant résume les principales similitudes et différences entre .NET Remoting et WCF.  
  
||.NET Remoting|WCF|  
|-|-------------------|---------|  
|Type de serveur|Sous-classe MarshalByRefObject|Marquer avec l'attribut [ServiceContract]|  
|Opérations de service|Méthodes publiques sur le type de serveur|Marquer avec l'attribut [OperationContract]|  
|Sérialisation|ISerializable ou [Serializable]|DataContractSerializer ou XmlSerializer|  
|Objets passés|Par valeur ou par référence|Par valeur uniquement|  
|Erreurs/exceptions|Toute exception sérialisable|FaultContract\<TDetail>|  
|Objets proxy clients|Proxys transparents fortement typés créés automatiquement à partir de MarshalByRefObjects|Des procurations fortement tapées sont générées\<à la demande à l’aide de ChannelFactory TChannel>|  
|Plateforme requise|Le client et le serveur doivent utiliser un système d'exploitation Microsoft et .NET|Multiplateforme|  
|Format de message|Privé|Normalisé (SOAP, WS-*, etc.)|  
  
### <a name="server-implementation-comparison"></a>Comparaison de l'implémentation serveur  
  
#### <a name="creating-a-server-in-net-remoting"></a>Création d'un serveur dans .NET Remoting  
 Les types de serveur .NET Remoting doivent dériver de MarshalByRefObject et définir des méthodes que le client peut appeler, comme celle-ci :  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Les méthodes publiques de ce type de serveur constituent le contrat public à disposition des clients.  Il n'y a pas de séparation entre l'interface publique du serveur et son implémentation : un seul type gère les deux.  
  
 Une fois le type de serveur défini, il peut être mis à disposition des clients, comme dans l'exemple suivant :  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Vous pouvez mettre à disposition le type Remoting en tant que serveur de plusieurs façons, notamment à l'aide de fichiers de configuration. Il s'agit là d'un exemple parmi d'autres.  
  
#### <a name="creating-a-server-in-wcf"></a>Création d'un serveur dans WCF  
 L'étape équivalente dans WCF implique la création de deux types : le « contrat de service » public et l'implémentation concrète. Le premier type est déclaré en tant qu'interface marquée avec [ServiceContract]. Les méthodes à disposition des clients sont marquées avec [OperationContract] :  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 L'implémentation du serveur est définie dans une classe concrète distincte, comme dans l'exemple suivant :  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Une fois ces types définis, le serveur WCF peut être mis à disposition des clients, comme dans l'exemple suivant :  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> TCP est utilisé dans les deux exemples pour qu'ils soient les plus semblables possible. Consultez les procédures pas à pas des scénarios figurant plus loin dans cette rubrique pour obtenir des exemples d'utilisation du protocole HTTP.  
  
 Vous pouvez configurer et héberger des services WCF de plusieurs façons. Cet exemple, qui illustre ce que l'on appelle l'auto-hébergement, n'est qu'un exemple parmi d'autres. Pour plus d'informations, voir les rubriques suivantes :  
  
- [Guide pratique pour définir un contrat de service](how-to-define-a-wcf-service-contract.md)  
  
- [Configuration des services à l'aide de fichiers de configuration](configuring-services-using-configuration-files.md)  
  
- [Hébergement de services](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Comparaison de l'implémentation client  
  
#### <a name="creating-a-client-in-net-remoting"></a>Création d'un client dans .NET Remoting  
 Une fois un objet serveur .NET Remoting mis à disposition, il peut être consommé par des clients, comme dans l'exemple suivant :  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 L'instance de RemotingServer retournée à partir d'Activator.GetObject() est désignée sous le terme de « proxy transparent ». Elle implémente l'API publique pour le type RemotingServer sur le client, mais toutes les méthodes appellent l'objet serveur en cours d'exécution dans un ordinateur ou un processus différent.  
  
#### <a name="creating-a-client-in-wcf"></a>Création d'un client dans WCF  
 L'étape équivalente dans WCF implique l'utilisation d'une fabrique de canaux pour créer explicitement le proxy. Comme dans Remoting, l'objet proxy peut être utilisé pour appeler des opérations sur le serveur, ce qu'illustre l'exemple suivant :  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Cet exemple montre la programmation au niveau du canal, car elle présente plus de similitudes avec l'exemple Remoting. L’approche **Add Service Reference** dans Visual Studio est également disponible et génère du code pour simplifier la programmation des clients. Pour plus d'informations, voir les rubriques suivantes :  
  
- [Programmation du client au niveau du canal](./extending/client-channel-level-programming.md)  
  
- [Comment : ajouter, mettre à jour ou supprimer une référence de service](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Utilisation de la sérialisation  
 Bien que .NET Remoting et WCF utilisent tous deux la sérialisation pour envoyer des objets entre le client et le serveur, il existe des différences importantes :  
  
1. Les conventions et sérialiseurs utilisés pour indiquer les éléments à sérialiser ne sont pas les mêmes.  
  
2. .NET Remoting prend en charge la sérialisation « par référence ». Celle-ci permet d'accéder à une méthode ou à une propriété située sur une couche et d'exécuter du code sur l'autre couche, au-delà des limites de sécurité. Cette fonctionnalité présente des failles de sécurité. C'est l'une des principales raisons pour lesquelles les points de terminaison Remoting ne doivent jamais être exposés à des clients non approuvés.  
  
3. La sérialisation utilisée par Remoting fonctionne par exclusion (les éléments à ne pas sérialiser sont exclus explicitement), tandis que la sérialisation WCF fonctionne par inclusion (les éléments à sérialiser sont marqués explicitement).  
  
#### <a name="serialization-in-net-remoting"></a>Sérialisation dans .NET Remoting  
 .NET Remoting prend en charge deux méthodes pour sérialiser et désérialiser des objets entre le client et le serveur :  
  
- *Par valeur* - les valeurs de l’objet sont sérialisées au-delà des frontières de niveau, et une nouvelle instance de cet objet est créé sur l’autre niveau. Tous les appels aux méthodes ou aux propriétés de cette nouvelle instance s'exécutent uniquement au niveau local et n'affectent pas la couche ou l'objet d'origine.  
  
- *Par référence* , une « référence d’objet » spéciale est sérialisée au-delà des frontières de niveau. Quand une couche interagit avec les méthodes ou les propriétés de cet objet, elle communique avec l'objet d'origine situé sur la couche d'origine. Les objets par référence peuvent circuler dans les deux sens : du serveur au client ou du client au serveur.  
  
 Les types par valeur dans Remoting sont marqués avec l'attribut [Serializable] ou implémentent ISerializable, comme dans l'exemple suivant :  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Les types par référence dérivent de la classe MarshalByRefObject, comme dans l’exemple suivant :  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Il est extrêmement important de comprendre les implications des objets par référence de Remoting. Si une couche (client ou serveur) envoie un objet par référence à l'autre couche, tous les appels de méthode s'exécutent sur la couche qui possède l'objet. Par exemple, un client appelant des méthodes sur un objet par référence retourné par le serveur exécute le code sur le serveur. De même, un serveur appelant des méthodes sur un objet par référence fourni par le client exécute le code sur le client. Pour cette raison, il est recommandé d'utiliser .NET Remoting uniquement dans des environnements entièrement fiables. Le fait d'exposer un point de terminaison .NET Remoting public à des clients non approuvés rend un serveur Remoting vulnérable aux attaques.  
  
#### <a name="serialization-in-wcf"></a>Sérialisation dans WCF  
 WCF prend uniquement en charge la sérialisation par valeur. La méthode la plus couramment employée pour définir un type à échanger entre le client et le serveur est semblable à celle présentée dans l'exemple suivant :  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 L'attribut [DataContract] identifie ce type comme pouvant être sérialisé et désérialisé entre le client et le serveur. L'attribut [DataMember] identifie les propriétés ou les champs individuels à sérialiser.  
  
 Quand WCF envoie un objet d'une couche à l'autre, il sérialise uniquement les valeurs et crée une instance de l'objet sur l'autre couche. Les interactions avec les valeurs de l'objet s'effectuent uniquement au niveau local ; contrairement aux objets par référence .NET Remoting, aucune communication n'a lieu avec l'autre couche. Pour plus d’informations, voir [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Capacités de gestion des exceptions  
  
#### <a name="exceptions-in-net-remoting"></a>Exceptions dans .NET Remoting  
 Les exceptions levées par un serveur Remoting sont sérialisées, envoyées au client et levées localement sur le client comme n'importe quelle autre exception. Vous pouvez créer des exceptions personnalisées en définissant une sous-classe du type Exception et en la marquant avec [Serializable].   La plupart des exceptions d'infrastructure étant déjà marquées de cette manière, elles peuvent être levées par le serveur, sérialisées et levées à nouveau sur le client. Bien que cette conception présente des avantages lors du développement, il est possible que des informations côté serveur soient transmises par inadvertance au client. C'est l'une des nombreuses raisons pour lesquelles Remoting doit uniquement être utilisé dans des environnements entièrement fiables.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Exceptions et erreurs dans WCF  
 Pour éviter la divulgation inopportune d'informations, WCF n'autorise pas le serveur à retourner des types d'exceptions arbitraires au client. Si une opération de service lève une exception inattendue, un FaultException à usage général est levé sur le client. Bien que cette exception ne comprenne pas d'informations sur la raison ou l'emplacement du problème, elle suffit à certaines applications. Pour communiquer des informations d'erreur plus détaillées au client, les applications doivent définir un contrat d'erreur.  
  
 Pour cela, vous devez d'abord créer un type [DataContract] qui contiendra les informations d'erreur.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Spécifiez le contrat d'erreur à utiliser pour chaque opération de service.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Le serveur signale les conditions d'erreur en levant un FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 Chaque fois que le client effectue une demande au serveur, il peut intercepter les erreurs comme des exceptions normales.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Pour plus d'informations sur les contrats d'erreur, consultez <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
  
#### <a name="security-in-net-remoting"></a>Sécurité dans .NET Remoting  
 Certains canaux .NET Remoting prennent en charge des fonctionnalités de sécurité telles que l'authentification et le chiffrement au niveau de la couche du canal (IPC et TCP). Le canal HTTP s'appuie sur les services Internet (IIS) pour procéder à l'authentification et au chiffrement. Toutefois, vous devez considérer .NET Remoting comme un protocole de communication non sécurisé et l'utiliser uniquement dans des environnements entièrement fiables. N'exposez jamais un point de terminaison Remoting public à Internet ou à des clients non approuvés.  
  
#### <a name="security-in-wcf"></a>Sécurité dans WCF  
 WCF a été conçu dans une optique de sécurité, en partie pour résoudre les types de vulnérabilités associées à .NET Remoting. Outre la sécurité au niveau du transport et des messages, WCF offre de nombreuses options en ce qui concerne l'authentification, l'autorisation, le chiffrement, etc. Pour plus d'informations, voir les rubriques suivantes :  
  
- [Sécurité](./feature-details/security.md)  
  
- [Orientation de sécurité WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migration vers WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Pourquoi effectuer la migration de Remoting vers WCF ?  
  
- **.NET Remoting est un produit hérité.** Comme décrit dans [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), il est considéré comme un produit hérité et n’est pas recommandé pour le nouveau développement. Il est recommandé d'utiliser WCF ou l'API Web ASP.NET pour les applications nouvelles et existantes.  
  
- **WCF utilise des normes multiplateformes.** Conçu pour mettre en avant l'interopérabilité multiplateforme, WCF prend en charge de nombreuses normes (SOAP, WS-Security, WS-Trust, etc.). Un service WCF peut interagir avec des clients en cours d'exécution sur des systèmes d'exploitation autres que Windows. La remotage a été conçue principalement pour les environnements où les applications serveur et client fonctionnent à l’aide de .NET Framework sur un système d’exploitation Windows.
  
- **WCF intègre des mesures de sécurité.** WCF a été conçu avec la sécurité à l’esprit et offre de nombreuses options pour l’authentification, la sécurité du niveau de transport, la sécurité au niveau du message, etc. La remotage a été conçue pour faciliter l’interopération des applications, mais n’a pas été conçue pour être sécurisée dans des environnements non fiables. De par sa conception, WCF fonctionne dans les environnements approuvés et non approuvés.  
  
### <a name="migration-recommendations"></a>Recommandations en matière de migration  
 Voici les étapes recommandées pour effectuer la migration de Remoting vers WCF :  
  
- **Créer le contrat de service.** Définissez vos types d'interface de service et marquez-les avec l'attribut [ServiceContract]. Marquez toutes les méthodes que les clients peuvent appeler avec [OperationContract].  
  
- **Créez le contrat de données.** Définissez les types de données échangées entre le serveur et le client, puis marquez-les avec l'attribut [DataContract]. Marquez tous les champs et propriétés que le client pourra utiliser avec [DataMember].  
  
- **Créer le contrat d'erreur (facultatif).** Créez les types échangés entre le client et le serveur en cas d'erreurs. Marquez ces types avec [DataContract] et [DataMember] pour les rendre sérialisables. Concernant les opérations de service marquées avec [OperationContract], marquez-les aussi avec [FaultContract] pour indiquer les erreurs qu'elles peuvent retourner.  
  
- **Configurer et héberger le service.** Une fois le contrat de service créé, l’étape suivante consiste à configurer une liaison pour exposer le service à un point de terminaison. Pour plus d’informations, voir [Points d’arrivée : Adresses, liaisons et contrats](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 À l'issue de la migration d'une application Remoting vers WCF, il est toujours important de supprimer les dépendances à .NET Remoting. Cela permet de s'assurer que toutes les vulnérabilités de Remoting sont supprimées de l'application. Notamment :  
  
- **Cesser d'utiliser MarshalByRefObject.** Le type MarshalByRefObject concerne uniquement Remoting et n’est pas utilisé par WCF. Les types d’applications qui définissent des sous-classes de MarshalByRefObject doivent être supprimés ou modifiés.  
  
- **Cesser d'utiliser [Serializable] et ISerializable.** Conçus à l'origine pour sérialiser les types dans les environnements fiables, l'attribut [Serializable] et l'interface ISerializable sont utilisés par Remoting. La sérialisation WCF s'appuie sur les types marqués avec [DataContract] et [DataMember]. Les types de données utilisés par une application doivent être modifiés afin d'utiliser [DataContract] et non l'interface ISerializable ou [Serializable].  
  
### <a name="migration-scenarios"></a>Scénarios de migration  
 Nous allons à présent voir comment transposer des scénarios Remoting courants suivants dans WCF :  
  
1. Le serveur retourne un objet par valeur au client  
  
2. Le serveur retourne un objet par référence au client  
  
3. Le client envoie un objet par valeur au serveur  
  
> [!NOTE]
> L'envoi d'un objet par référence du client vers le serveur n'est pas autorisé dans WCF.  
  
 Quand vous lisez ces scénarios, tenez compte du fait que nos interfaces de planning de référence pour .NET Remoting ressemblent à l’exemple suivant. L'implémentation de .NET Remoting n'est pas importante ici, car notre objectif est de montrer comment utiliser WCF pour implémenter des fonctionnalités équivalentes.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scénario 1 : service retournant un objet par valeur  
 Ce scénario présente un serveur qui retourne un objet par valeur au client. WCF retourne toujours les objets du serveur par valeur. Les étapes suivantes décrivent donc la création d'un service WCF normal.  
  
1. Commencez par définir une interface publique pour le service WCF et marquez-la avec l'attribut [ServiceContract]. [OperationContract] nous permet d'identifier les méthodes côté serveur qui seront appelées par notre client.  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. L'étape suivante consiste à créer le contrat de données pour ce service. Pour cela, nous créons des classes (et non des interfaces) marquées avec l'attribut [DataContract]. Les propriétés ou champs individuels qui doivent être visibles au client et au serveur sont marqués avec [DataMember]. Pour autoriser les types dérivés, nous devons les identifier à l'aide de l'attribut [KnownType]. Les seuls types dont WCF autorise la sérialisation ou la désérialisation pour ce service sont ceux contenus dans l'interface de service et ces « types connus ». Toute tentative visant à échanger un autre type ne figurant pas dans cette liste sera rejetée.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Ensuite, nous devons fournir l'implémentation de l'interface de service.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. Pour exécuter le service WCF, nous devons déclarer un point de terminaison qui expose cette interface de service à une URL spécifique à l'aide d'une liaison WCF spécifique. Pour cela, il suffit généralement d'ajouter les sections suivantes au fichier web.config du projet serveur.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. Le service WCF peut ensuite être démarré à l'aide du code suivant :  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Quand ServiceHost démarre, il utilise le fichier web.config pour établir le contrat, la liaison et le point de terminaison appropriés. Pour plus d’informations sur les fichiers de configuration, voir [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md). On parle d'auto-hébergement pour désigner ce type de démarrage du serveur. Pour en savoir plus sur d’autres choix pour l’hébergement des services WCF, consultez [Hosting Services](./hosting-services.md).  
  
6. Le fichier app.config du projet client doit déclarer les informations de liaison correspondante pour le point de terminaison du service. La façon la plus simple de le faire dans Visual Studio est d’utiliser **Add Service Reference**, qui mettra automatiquement à jour le fichier app.config. Vous pouvez également ajouter manuellement ces mêmes modifications.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Pour plus d’informations sur l’utilisation **de Add Service Reference**, voir comment : [Ajouter, mettre à jour ou supprimer une référence de service](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Nous pouvons maintenant appeler le service WCF à partir du client. Pour cela, nous créons une fabrique de canaux pour ce service, nous demandons un canal, puis nous appelons directement la méthode que nous voulons sur ce canal. Si nous pouvons procéder de la sorte, c'est parce que le canal implémente l'interface du service et qu'il gère pour nous la logique sous-jacente des demandes/réponses. La valeur de retour de cet appel de méthode est la copie désérialisée de la réponse du serveur.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Les objets retournés par WCF du serveur au client sont toujours par valeur. Les objets sont des copies désérialisées des données envoyées par le serveur. Le client peut appeler des méthodes sur ces copies locales sans aucun risque d'appeler le code serveur via des rappels.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scénario 2 : serveur retournant un objet par référence  
 Ce scénario présente un serveur qui fournit un objet au client par référence. Dans .NET Remoting, ceci est géré automatiquement pour n’importe quel type dérivé de MarshalByRefObject, qui est sérialisé par référence. Autoriser plusieurs clients à avoir des objets côté serveur de session indépendants est un exemple de ce scénario. Comme mentionné précédemment, les objets retournés par un service WCF sont toujours des objets par valeur. Il n'y a donc pas d'équivalent direct à un objet par référence, mais vous pouvez obtenir des résultats semblables à la sémantique par référence en utilisant un objet <xref:System.ServiceModel.EndpointAddress10>. Il s'agit d'un objet par valeur sérialisable qui peut être utilisé par le client pour obtenir un objet par référence de session sur le serveur. Cela permet la prise en charge de plusieurs clients avec des objets côté serveur de session indépendants.  
  
1. Tout d'abord, nous devons définir un contrat de service WCF qui correspond à l'objet de session proprement dit.  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > Notez que l'objet de session est marqué avec [ServiceContract], ce qui en fait une interface de service WCF normale. Le fait de définir la propriété SessionMode indique qu'il s'agit d'un service de session. Dans WCF, une session est une façon de mettre en corrélation plusieurs messages envoyés entre deux points de terminaison. Cela signifie qu'une fois qu'un client obtient une connexion à ce service, une session est établie entre le client et le serveur. Le client utilisera une seule instance de l'objet côté serveur pour toutes ses interactions au sein de cette session unique.  
  
2. Nous devons ensuite fournir l'implémentation de l'interface du service. En spécifiant [ServiceBehavior] et en définissant InstanceContextMode, nous indiquons à WCF que nous souhaitons utiliser une instance unique de ce type pour chaque session.  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. Nous devons à présent trouver le moyen d'obtenir une instance de cet objet de session. Pour cela, nous créons une autre interface de service WCF qui retourne un objet EndpointAddress10. Il s'agit d'une forme sérialisable d'un point de terminaison que le client peut utiliser pour créer l'objet de session.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     Puis nous implémentons ce service WCF :  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =
               new ChannelFactory<ISessionBoundObject>("sessionbound");  

           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     Cette implémentation gère une fabrique de canaux singleton pour créer des objets de session. Quand GetInstanceAddress() est appelé, il crée un canal et un objet EndpointAddress10 qui pointe vers l'adresse distante associée à ce canal. EndpointAddress10 est simplement un type de données qui peut être retourné au client par valeur.  
  
4. Pour modifier le fichier de configuration du serveur, nous devons effectuer les deux tâches suivantes, comme le montre l'exemple ci-dessous :  
  
    1. Déclarez \<un client> section qui décrit le point de terminaison de l’objet de session. Cette opération est nécessaire, car le serveur joue également le rôle de client dans cette situation.  
  
    2. Déclarez les points de terminaison pour la fabrique et l'objet de session. Cette opération est nécessaire afin de permettre au client de communiquer avec les points de terminaison du service pour acquérir l'objet EndpointAddress10 et créer le canal de session.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Ensuite, nous pouvons démarrer ces services :  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Nous configurons le client en déclarant ces mêmes points de terminaison dans le fichier app.config de son projet.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. Pour créer et utiliser cet objet de session, le client doit effectuer les opérations suivantes :  
  
    1. Créer un canal jusqu'au service ISessionBoundFactory  
  
    2. Utiliser ce canal pour appeler ce service afin d'obtenir un objet EndpointAddress10  
  
    3. Utiliser l'objet EndpointAddress10 pour créer un canal et obtenir un objet de session  
  
    4. Interagir avec l'objet de session pour montrer qu'il s'agit de la même instance sur plusieurs appels  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF retourne toujours les objets par valeur, mais il est possible de prendre en charge l'équivalent de la sémantique par référence en utilisant l'objet EndpointAddress10. Le client peut ainsi demander une instance de service WCF de session avec laquelle il peut ensuite interagir comme n'importe quel autre service WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scénario 3 : envoi par le client au serveur d'une instance par valeur  
 Ce scénario présente un client qui envoie une instance d'objet non primitif au serveur par valeur. Étant donné que WCF envoie uniquement les objets par valeur, ce scénario illustre une utilisation normale de WCF.  
  
1. Utilisez le même service WCF que celui du scénario 1.  
  
2. Utilisez le client pour créer un objet par valeur (Customer), créez un canal pour communiquer avec le service ICustomerService, puis envoyez-lui l'objet.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     L'objet Customer est sérialisé, puis envoyé au service où il est désérialisé en nouvelle copie de cet objet.  
  
    > [!NOTE]
    > Ce code illustre également l'envoi d'un type dérivé (PremiumCustomer). L'interface de service attend un objet Customer, mais l'attribut [KnownType] sur la classe Customer indique que PremiumCustomer est également autorisé. Les tentatives de WCF de sérialisation ou de désérialisation de tout autre type via cette interface de service échouent.  
  
 Dans WCF, les données sont normalement échangées par valeur. Cela garantit que l'appel de méthodes sur l'un de ces objets de données s'exécute uniquement au niveau local (le code sur l'autre couche n'est pas appelé). Bien qu’il soit possible d’atteindre quelque chose comme des objets de référence retournés *du* serveur, il n’est pas possible pour un client de passer un *objet* de référence par le serveur. Une conversation entre un client et un serveur peut être effectuée dans WCF à l'aide d'un service duplex. Pour plus d’informations, voir [Duplex Services](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Résumé  
 .NET Remoting est une infrastructure de communication destinée à être utilisée uniquement dans des environnements entièrement fiables. Il s'agit d'un produit hérité qui est uniquement pris en charge à des fins de compatibilité descendante. Il ne doit pas être utilisé pour développer de nouvelles applications. À l'inverse, WCF a été conçu dans une optique de sécurité et est recommandé pour les applications nouvelles et existantes. Microsoft recommande de migrer les applications Remoting existantes vers WCF ou l'API Web ASP.NET.
