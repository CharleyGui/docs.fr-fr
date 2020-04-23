---
title: 'Comment : migrer DCOM de code managé vers WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181393"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Comment : migrer DCOM de code managé vers WCF
Pour des raisons de sécurité, il est recommandé d'utiliser Windows Communication Foundation (WCF) plutôt que le modèle DCOM pour les appels de code managé entre serveurs et clients dans un environnement distribué. Cet article explique comment migrer du code DCOM vers WCF pour les scénarios suivants.  
  
- Le service distant retourne un objet par valeur au client  
  
- Le client envoie un objet par valeur au service distant  
  
- Le service distant retourne un objet par référence au client  
  
 Pour des raisons de sécurité, l'envoi d'un objet par référence à partir du client vers le service n'est pas autorisé dans WCF. Une conversation entre un client et un serveur peut être effectuée dans WCF à l'aide d'un service duplex.  Pour plus d’informations sur les services duplex, consultez [Services duplex](../wcf/feature-details/duplex-services.md).  
  
 Pour plus d’informations sur la création de services WCF et de clients pour ces services, consultez [Programmation WCF de base](../wcf/basic-wcf-programming.md), [Conception et implémentation de services](../wcf/designing-and-implementing-services.md) et [Génération de clients](../wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Exemple de code DCOM  
 Pour ces scénarios, les interfaces DCOM qui sont illustrées à l'aide de WCF possèdent la structure suivante :  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a>Le service retourne un objet par valeur  
 Pour ce scénario, vous effectuez un appel à un service et sa méthode renvoie un objet qui est passé par valeur du serveur au client. Ce scénario représente l'appel COM suivant :  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 Dans ce scénario, le client reçoit une copie désérialisée d'un objet à partir du service distant. Le client peut interagir avec cette copie locale sans effectuer de rappel au service.  En d'autres termes, le client a la garantie que le service ne sera impliqué en aucune façon quand les méthodes de la copie locale seront appelées. WCF retourne toujours les objets à partir du service par valeur. Les étapes suivantes décrivent donc la création d'un service WCF normal.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Étape 1 : Définir l'interface du service WCF  
 Définissez une interface publique pour le service WCF et marquez-la avec l'attribut [<xref:System.ServiceModel.ServiceContractAttribute>].  Marquez les méthodes que vous souhaitez exposer aux clients avec l'attribut [<xref:System.ServiceModel.OperationContractAttribute>]. L'exemple suivant illustre l'utilisation de ces attributs pour identifier l'interface côté serveur et les méthodes d'interface qu'un client peut appeler. La méthode utilisée pour ce scénario est affichée en gras.  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a>Étape 2 : Définir le contrat de données  
 Ensuite, vous devez créer un contrat de données pour le service, qui décrira comment les données seront échangées entre le service et ses clients.  Les classes décrites dans le contrat de données doivent être marquées avec l'attribut [<xref:System.Runtime.Serialization.DataContractAttribute>]. Les propriétés ou champs individuels que vous souhaitez voir apparaître sur le client et le serveur doivent être marqués avec l’attribut [<xref:System.Runtime.Serialization.DataMemberAttribute>]. Si vous souhaitez autoriser des types dérivés d’une classe dans le contrat de données, vous devez les identifier avec l’attribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>]. WCF va uniquement sérialiser ou désérialiser les types de l'interface de service et les types identifiés comme connus. Si vous essayez d'utiliser un type qui n'est pas connu, une exception se produit.  
  
 Pour plus d’informations sur les contrats de données, consultez [Contrats de données](../wcf/samples/data-contracts.md).  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a>Étape 3 : Implémenter le service WCF  
 Ensuite, vous devez implémenter la classe du service WCF qui implémente l'interface que vous avez définie à l'étape précédente.  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a>Étape 4 : Configurer le service et le client  
 Pour exécuter un service WCF, vous devez déclarer un point de terminaison qui expose cette interface de service à une URL spécifique à l'aide d'une liaison WCF spécifique. Une liaison spécifie les détails relatifs au transport, à l’encodage et au protocole pour que le serveur et les clients puissent communiquer. En général, vous ajoutez des liaisons au fichier de configuration du projet de service (web.config). Le code suivant illustre une entrée de liaison pour l’exemple de service :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ensuite, vous devez configurer le client pour faire correspondre les informations de liaison spécifiées par le service. Pour ce faire, ajoutez le code suivant au fichier de configuration d'application (app.config) du client.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Étape 5 : Exécuter le service  
 Enfin, vous pouvez automatiquement l'héberger dans une application console en ajoutant les lignes suivantes à l'application de service, puis en démarrant l'application. Pour plus d’informations sur les autres méthodes d’hébergement d’une application de service WCF, consultez [Services d’hébergement](../wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Étape 6 : Appeler le service depuis le client  
 Pour appeler le service depuis le client, vous devez créer une fabrique de canaux pour le service et demander un canal, ce qui vous permettra d'appeler directement la méthode `GetCustomer` depuis le client. Le canal implémente l'interface du service et gère la logique sous-jacente de demande/réponse à votre place.  La valeur de retour de cet appel de méthode est la copie désérialisée de la réponse du service.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Le client envoie un objet par valeur au serveur  
 Dans ce scénario, le client envoie un objet au serveur par valeur. Cela signifie que le serveur reçoit une copie désérialisée de l'objet.  Le serveur peut appeler des méthodes de cette copie et avoir la garantie qu'il n'y aura aucun rappel dans le code client. Comme mentionné précédemment, les échanges WCF de données normaux sont par valeur.  Cela garantit que l'appel de méthodes sur l'un de ces objets s'exécutera uniquement localement et n'appellera pas le code du client.  
  
 Ce scénario représente l'appel de méthode COM suivant :  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Ce scénario utilise la même interface de service et le même contrat de données que ceux du premier exemple. De plus, le client et le service seront configurés de la même façon. Dans cet exemple, un canal est créé pour envoyer l'objet et l'exécuter de la même façon. Toutefois, pour cet exemple, vous allez créer un client qui appelle le service, en passant un objet par valeur. La méthode de service que le client appelle dans le contrat de service est affichée en gras :  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Ajouter le code au client qui envoie un objet par valeur  
 Le code suivant montre comment le client crée un nouvel objet Customer par valeur, et comment il crée un canal pour communiquer avec le service `ICustomerManager` et lui envoie l'objet Customer.  
  
 L'objet Customer sera sérialisé, puis envoyé au service, où il sera désérialisé par le service sous la forme d'une nouvelle copie de cet objet.  Toutes les méthodes que le service appelle sur cet objet ne s’exécuteront que localement sur le serveur. Il est important de noter que ce code illustre l’envoi d’un type dérivé (`PremiumCustomer`).  Le contrat de service attend un objet `Customer`, mais le contrat de données du service utilise l'attribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>] pour indiquer que `PremiumCustomer` est également autorisé.  Les tentatives de WCF de sérialisation ou de désérialisation de tout autre type via cette interface de service échoueront.  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a>Le service retourne un objet par référence  
 Pour ce scénario, l'application cliente effectue un appel au service distant et la méthode retourne un objet qui est passé par référence à partir du service au client.  
  
 Comme mentionné précédemment, les services WCF retournent toujours un objet par valeur.  Toutefois, vous pouvez obtenir un résultat similaire en utilisant la classe <xref:System.ServiceModel.EndpointAddress10>.  <xref:System.ServiceModel.EndpointAddress10> est un objet sérialisable par valeur qui peut être utilisé par le client pour obtenir un objet de session par référence sur le serveur.  
  
 Le comportement de l'objet par référence dans WCF illustré dans ce scénario est différent du comportement dans DCOM.  Dans DCOM, le serveur peut renvoyer un objet par référence au client directement, et le client peut appeler les méthodes de l'objet, qui s'exécuteront sur le serveur.  Dans WCF, toutefois, l'objet retourné est toujours par valeur.  Le client doit prendre cet objet par valeur, représenté par <xref:System.ServiceModel.EndpointAddress10>, et l'utiliser pour créer son propre objet de session par référence.  Les appels de méthode du client sur l'objet de session s'exécutent sur le serveur. En d'autres termes, cet objet par référence dans WCF est un service WCF normal qui est configuré pour être de session.  
  
 Dans WCF, une session est une façon de mettre en corrélation plusieurs messages envoyés entre deux points de terminaison.  Cela signifie qu'une fois qu'un client obtient une connexion à ce service, une session est établie entre le client et le serveur.  Le client utilisera une seule instance de l'objet côté serveur pour toutes ses interactions au sein de cette session unique. Les contrats de session WCF sont similaires aux modèles de demande/réponse réseau orientés connexion.  
  
 Ce scénario est représenté par la méthode DCOM suivante.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Étape 1: Définir l'interface et l'implémentation du service de session WCF  
 Tout d'abord, définissez une interface de service WCF contenant l'objet de session.  
  
 Dans ce code, l'objet de session est marqué avec l'attribut `ServiceContract`, qui l'identifie comme une interface de service WCF standard.  De plus, la propriété <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> est définie pour indiquer qu'il s'agira d'un service de session.  
  
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
  
 Le code suivant montre l'implémentation du service.  
  
 Le service est marqué avec l'attribut [ServiceBehavior]. Sa propriété InstanceContextMode a la valeur InstanceContextMode.PerSessions pour indiquer qu'une instance unique de ce type doit être créée pour chaque session.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Étape 2 : Définir le service de fabrique WCF pour l'objet de session  
 Le service qui crée l'objet de session doit être défini et implémenté. Le code suivant montre comment procéder. Ce code crée un autre service WCF qui retourne un objet <xref:System.ServiceModel.EndpointAddress10>.  Il s'agit d'une forme sérialisable d'un point de terminaison qui peut être utilisée pour créer l'objet de session.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Voici l’implémentation de ce service. Cette implémentation gère une fabrique de canaux singleton pour créer des objets de session.  Quand `GetInstanceAddress` est appelé, il crée un canal et un objet <xref:System.ServiceModel.EndpointAddress10> qui pointe vers l'adresse distante associée à ce canal.   <xref:System.ServiceModel.EndpointAddress10> est un type de données qui peut être renvoyé au client par valeur.
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Étape 3 : Configurer et démarrer les services WCF  
 Pour héberger ces services, vous devrez effectuer les ajouts suivants au fichier de configuration du serveur (web.config).  
  
1. Ajoutez une section `<client>` qui décrive le point de terminaison de l'objet de session.  Dans ce scénario, le serveur agit comme un client et doit être configuré pour rendre ceci possible.  
  
2. Dans la section `<services>`, déclarez les points de terminaison de service pour la fabrique et l'objet de session.  Cela permet au client de communiquer avec les points de terminaison du service, d'acquérir <xref:System.ServiceModel.EndpointAddress10> et de créer le canal de session.  
  
 Voici un exemple de fichier de configuration avec ces paramètres :  
  
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
  
 Ajoutez les lignes suivantes à une application console pour auto-héberger le service, puis démarrez l'application.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Étape 4 : Configurer le client et appeler le service  
 Configurez le client pour communiquer avec les services WCF en ajoutant les entrées suivantes dans le fichier de configuration d'application du projet (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
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
  
 Pour appeler le service, ajoutez le code au client qui servira à effectuer ce qui suit :  
  
1. Créer un canal vers le service `ISessionBoundFactory`.  
  
2. Utiliser le canal pour appeler le service `ISessionBoundFactory` et obtenir un objet <xref:System.ServiceModel.EndpointAddress10>.  
  
3. Utiliser <xref:System.ServiceModel.EndpointAddress10> pour créer un canal et obtenir un objet de session.  
  
4. Appeler les méthodes `SetCurrentValue` et `GetCurrentValue` pour montrer que la même instance d'objet est utilisée pour plusieurs appels.  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](../wcf/basic-wcf-programming.md)
- [Conception et implémentation de services](../wcf/designing-and-implementing-services.md)
- [Génération de clients](../wcf/building-clients.md)
- [Services duplex](../wcf/feature-details/duplex-services.md)
