---
title: 'Procédure : Migrer du code DCOM managé vers WCF'
description: Migrez les appels de code managé DCOM (Distributed Component Object Model) entre les serveurs et les clients vers Windows Communication Foundation (WCF).
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: cc6ac1dd01e17bb184d1f1faca372134d6130d33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619089"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="9fef9-103">Procédure : Migrer du code DCOM managé vers WCF</span><span class="sxs-lookup"><span data-stu-id="9fef9-103">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="9fef9-104">Pour des raisons de sécurité, il est recommandé d'utiliser Windows Communication Foundation (WCF) plutôt que le modèle DCOM pour les appels de code managé entre serveurs et clients dans un environnement distribué.</span><span class="sxs-lookup"><span data-stu-id="9fef9-104">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="9fef9-105">Cet article explique comment migrer du code DCOM vers WCF pour les scénarios suivants.</span><span class="sxs-lookup"><span data-stu-id="9fef9-105">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="9fef9-106">Le service distant retourne un objet par valeur au client</span><span class="sxs-lookup"><span data-stu-id="9fef9-106">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="9fef9-107">Le client envoie un objet par valeur au service distant</span><span class="sxs-lookup"><span data-stu-id="9fef9-107">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="9fef9-108">Le service distant retourne un objet par référence au client</span><span class="sxs-lookup"><span data-stu-id="9fef9-108">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="9fef9-109">Pour des raisons de sécurité, l'envoi d'un objet par référence à partir du client vers le service n'est pas autorisé dans WCF.</span><span class="sxs-lookup"><span data-stu-id="9fef9-109">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="9fef9-110">Une conversation entre un client et un serveur peut être effectuée dans WCF à l'aide d'un service duplex.</span><span class="sxs-lookup"><span data-stu-id="9fef9-110">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="9fef9-111">Pour plus d’informations sur les services duplex, consultez [Services duplex](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fef9-111">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="9fef9-112">Pour plus d’informations sur la création de services WCF et de clients pour ces services, consultez [Programmation WCF de base](../wcf/basic-wcf-programming.md), [Conception et implémentation de services](../wcf/designing-and-implementing-services.md) et [Génération de clients](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9fef9-112">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="9fef9-113">Exemple de code DCOM</span><span class="sxs-lookup"><span data-stu-id="9fef9-113">DCOM example code</span></span>  
 <span data-ttu-id="9fef9-114">Pour ces scénarios, les interfaces DCOM qui sont illustrées à l'aide de WCF possèdent la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="9fef9-114">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="9fef9-115">Le service retourne un objet par valeur</span><span class="sxs-lookup"><span data-stu-id="9fef9-115">The service returns an object by-value</span></span>  
 <span data-ttu-id="9fef9-116">Pour ce scénario, vous effectuez un appel à un service et sa méthode renvoie un objet qui est passé par valeur du serveur au client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-116">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="9fef9-117">Ce scénario représente l'appel COM suivant :</span><span class="sxs-lookup"><span data-stu-id="9fef9-117">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="9fef9-118">Dans ce scénario, le client reçoit une copie désérialisée d'un objet à partir du service distant.</span><span class="sxs-lookup"><span data-stu-id="9fef9-118">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="9fef9-119">Le client peut interagir avec cette copie locale sans effectuer de rappel au service.</span><span class="sxs-lookup"><span data-stu-id="9fef9-119">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="9fef9-120">En d'autres termes, le client a la garantie que le service ne sera impliqué en aucune façon quand les méthodes de la copie locale seront appelées.</span><span class="sxs-lookup"><span data-stu-id="9fef9-120">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="9fef9-121">WCF retourne toujours les objets à partir du service par valeur. Les étapes suivantes décrivent donc la création d'un service WCF normal.</span><span class="sxs-lookup"><span data-stu-id="9fef9-121">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="9fef9-122">Étape 1 : Définir l'interface du service WCF</span><span class="sxs-lookup"><span data-stu-id="9fef9-122">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="9fef9-123">Définissez une interface publique pour le service WCF et marquez-la avec l'attribut [<xref:System.ServiceModel.ServiceContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="9fef9-123">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="9fef9-124">Marquez les méthodes que vous souhaitez exposer aux clients avec l'attribut [<xref:System.ServiceModel.OperationContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="9fef9-124">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="9fef9-125">L'exemple suivant illustre l'utilisation de ces attributs pour identifier l'interface côté serveur et les méthodes d'interface qu'un client peut appeler.</span><span class="sxs-lookup"><span data-stu-id="9fef9-125">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="9fef9-126">La méthode utilisée pour ce scénario est affichée en gras.</span><span class="sxs-lookup"><span data-stu-id="9fef9-126">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="9fef9-127">Étape 2 : Définir le contrat de données</span><span class="sxs-lookup"><span data-stu-id="9fef9-127">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="9fef9-128">Ensuite, vous devez créer un contrat de données pour le service, qui décrira comment les données seront échangées entre le service et ses clients.</span><span class="sxs-lookup"><span data-stu-id="9fef9-128">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="9fef9-129">Les classes décrites dans le contrat de données doivent être marquées avec l'attribut [<xref:System.Runtime.Serialization.DataContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="9fef9-129">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="9fef9-130">Les propriétés ou champs individuels que vous souhaitez voir apparaître sur le client et le serveur doivent être marqués avec l’attribut [<xref:System.Runtime.Serialization.DataMemberAttribute>].</span><span class="sxs-lookup"><span data-stu-id="9fef9-130">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="9fef9-131">Si vous souhaitez autoriser des types dérivés d’une classe dans le contrat de données, vous devez les identifier avec l’attribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>].</span><span class="sxs-lookup"><span data-stu-id="9fef9-131">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="9fef9-132">WCF va uniquement sérialiser ou désérialiser les types de l'interface de service et les types identifiés comme connus.</span><span class="sxs-lookup"><span data-stu-id="9fef9-132">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="9fef9-133">Si vous essayez d'utiliser un type qui n'est pas connu, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="9fef9-133">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="9fef9-134">Pour plus d’informations sur les contrats de données, consultez [Contrats de données](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9fef9-134">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="9fef9-135">Étape 3 : Implémenter le service WCF</span><span class="sxs-lookup"><span data-stu-id="9fef9-135">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="9fef9-136">Ensuite, vous devez implémenter la classe du service WCF qui implémente l'interface que vous avez définie à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="9fef9-136">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="9fef9-137">Étape 4 : Configurer le service et le client</span><span class="sxs-lookup"><span data-stu-id="9fef9-137">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="9fef9-138">Pour exécuter un service WCF, vous devez déclarer un point de terminaison qui expose cette interface de service à une URL spécifique à l'aide d'une liaison WCF spécifique.</span><span class="sxs-lookup"><span data-stu-id="9fef9-138">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="9fef9-139">Une liaison spécifie les détails relatifs au transport, à l’encodage et au protocole pour que le serveur et les clients puissent communiquer.</span><span class="sxs-lookup"><span data-stu-id="9fef9-139">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="9fef9-140">En général, vous ajoutez des liaisons au fichier de configuration du projet de service (web.config).</span><span class="sxs-lookup"><span data-stu-id="9fef9-140">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="9fef9-141">Le code suivant illustre une entrée de liaison pour l’exemple de service :</span><span class="sxs-lookup"><span data-stu-id="9fef9-141">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="9fef9-142">Ensuite, vous devez configurer le client pour faire correspondre les informations de liaison spécifiées par le service.</span><span class="sxs-lookup"><span data-stu-id="9fef9-142">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="9fef9-143">Pour ce faire, ajoutez le code suivant au fichier de configuration d'application (app.config) du client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-143">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="9fef9-144">Étape 5 : Exécuter le service</span><span class="sxs-lookup"><span data-stu-id="9fef9-144">Step 5: Run the service</span></span>  
 <span data-ttu-id="9fef9-145">Enfin, vous pouvez automatiquement l'héberger dans une application console en ajoutant les lignes suivantes à l'application de service, puis en démarrant l'application.</span><span class="sxs-lookup"><span data-stu-id="9fef9-145">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="9fef9-146">Pour plus d’informations sur les autres méthodes d’hébergement d’une application de service WCF, consultez [Services d’hébergement](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fef9-146">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="9fef9-147">Étape 6 : Appeler le service depuis le client</span><span class="sxs-lookup"><span data-stu-id="9fef9-147">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="9fef9-148">Pour appeler le service depuis le client, vous devez créer une fabrique de canaux pour le service et demander un canal, ce qui vous permettra d'appeler directement la méthode `GetCustomer` depuis le client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-148">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="9fef9-149">Le canal implémente l'interface du service et gère la logique sous-jacente de demande/réponse à votre place.</span><span class="sxs-lookup"><span data-stu-id="9fef9-149">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="9fef9-150">La valeur de retour de cet appel de méthode est la copie désérialisée de la réponse du service.</span><span class="sxs-lookup"><span data-stu-id="9fef9-150">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="9fef9-151">Le client envoie un objet par valeur au serveur</span><span class="sxs-lookup"><span data-stu-id="9fef9-151">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="9fef9-152">Dans ce scénario, le client envoie un objet au serveur par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-152">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="9fef9-153">Cela signifie que le serveur reçoit une copie désérialisée de l'objet.</span><span class="sxs-lookup"><span data-stu-id="9fef9-153">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="9fef9-154">Le serveur peut appeler des méthodes de cette copie et avoir la garantie qu'il n'y aura aucun rappel dans le code client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-154">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="9fef9-155">Comme mentionné précédemment, les échanges WCF de données normaux sont par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-155">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="9fef9-156">Cela garantit que l'appel de méthodes sur l'un de ces objets s'exécutera uniquement localement et n'appellera pas le code du client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-156">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="9fef9-157">Ce scénario représente l'appel de méthode COM suivant :</span><span class="sxs-lookup"><span data-stu-id="9fef9-157">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="9fef9-158">Ce scénario utilise la même interface de service et le même contrat de données que ceux du premier exemple.</span><span class="sxs-lookup"><span data-stu-id="9fef9-158">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="9fef9-159">De plus, le client et le service seront configurés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="9fef9-159">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="9fef9-160">Dans cet exemple, un canal est créé pour envoyer l'objet et l'exécuter de la même façon.</span><span class="sxs-lookup"><span data-stu-id="9fef9-160">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="9fef9-161">Toutefois, pour cet exemple, vous allez créer un client qui appelle le service, en passant un objet par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-161">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="9fef9-162">La méthode de service que le client appelle dans le contrat de service est affichée en gras :</span><span class="sxs-lookup"><span data-stu-id="9fef9-162">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="9fef9-163">Ajouter le code au client qui envoie un objet par valeur</span><span class="sxs-lookup"><span data-stu-id="9fef9-163">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="9fef9-164">Le code suivant montre comment le client crée un nouvel objet Customer par valeur, et comment il crée un canal pour communiquer avec le service `ICustomerManager` et lui envoie l'objet Customer.</span><span class="sxs-lookup"><span data-stu-id="9fef9-164">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="9fef9-165">L'objet Customer sera sérialisé, puis envoyé au service, où il sera désérialisé par le service sous la forme d'une nouvelle copie de cet objet.</span><span class="sxs-lookup"><span data-stu-id="9fef9-165">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="9fef9-166">Toutes les méthodes que le service appelle sur cet objet ne s’exécuteront que localement sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-166">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="9fef9-167">Il est important de noter que ce code illustre l’envoi d’un type dérivé (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="9fef9-167">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="9fef9-168">Le contrat de service attend un objet `Customer`, mais le contrat de données du service utilise l'attribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>] pour indiquer que `PremiumCustomer` est également autorisé.</span><span class="sxs-lookup"><span data-stu-id="9fef9-168">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="9fef9-169">Les tentatives de WCF de sérialisation ou de désérialisation de tout autre type via cette interface de service échoueront.</span><span class="sxs-lookup"><span data-stu-id="9fef9-169">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="9fef9-170">Le service retourne un objet par référence</span><span class="sxs-lookup"><span data-stu-id="9fef9-170">The service returns an object by reference</span></span>  
 <span data-ttu-id="9fef9-171">Pour ce scénario, l'application cliente effectue un appel au service distant et la méthode retourne un objet qui est passé par référence à partir du service au client.</span><span class="sxs-lookup"><span data-stu-id="9fef9-171">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="9fef9-172">Comme mentionné précédemment, les services WCF retournent toujours un objet par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-172">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="9fef9-173">Toutefois, vous pouvez obtenir un résultat similaire en utilisant la classe <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="9fef9-173">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="9fef9-174"><xref:System.ServiceModel.EndpointAddress10> est un objet sérialisable par valeur qui peut être utilisé par le client pour obtenir un objet de session par référence sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-174">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="9fef9-175">Le comportement de l'objet par référence dans WCF illustré dans ce scénario est différent du comportement dans DCOM.</span><span class="sxs-lookup"><span data-stu-id="9fef9-175">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="9fef9-176">Dans DCOM, le serveur peut renvoyer un objet par référence au client directement, et le client peut appeler les méthodes de l'objet, qui s'exécuteront sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-176">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="9fef9-177">Dans WCF, toutefois, l'objet retourné est toujours par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-177">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="9fef9-178">Le client doit prendre cet objet par valeur, représenté par <xref:System.ServiceModel.EndpointAddress10>, et l'utiliser pour créer son propre objet de session par référence.</span><span class="sxs-lookup"><span data-stu-id="9fef9-178">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="9fef9-179">Les appels de méthode du client sur l'objet de session s'exécutent sur le serveur. En d'autres termes, cet objet par référence dans WCF est un service WCF normal qui est configuré pour être de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-179">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="9fef9-180">Dans WCF, une session est une façon de mettre en corrélation plusieurs messages envoyés entre deux points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9fef9-180">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="9fef9-181">Cela signifie qu'une fois qu'un client obtient une connexion à ce service, une session est établie entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-181">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="9fef9-182">Le client utilisera une seule instance de l'objet côté serveur pour toutes ses interactions au sein de cette session unique.</span><span class="sxs-lookup"><span data-stu-id="9fef9-182">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="9fef9-183">Les contrats de session WCF sont similaires aux modèles de demande/réponse réseau orientés connexion.</span><span class="sxs-lookup"><span data-stu-id="9fef9-183">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="9fef9-184">Ce scénario est représenté par la méthode DCOM suivante.</span><span class="sxs-lookup"><span data-stu-id="9fef9-184">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="9fef9-185">Étape 1: Définir l'interface et l'implémentation du service de session WCF</span><span class="sxs-lookup"><span data-stu-id="9fef9-185">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="9fef9-186">Tout d'abord, définissez une interface de service WCF contenant l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-186">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="9fef9-187">Dans ce code, l'objet de session est marqué avec l'attribut `ServiceContract`, qui l'identifie comme une interface de service WCF standard.</span><span class="sxs-lookup"><span data-stu-id="9fef9-187">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="9fef9-188">De plus, la propriété <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> est définie pour indiquer qu'il s'agira d'un service de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-188">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="9fef9-189">Le code suivant montre l'implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="9fef9-189">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="9fef9-190">Le service est marqué avec l'attribut [ServiceBehavior]. Sa propriété InstanceContextMode a la valeur InstanceContextMode.PerSessions pour indiquer qu'une instance unique de ce type doit être créée pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-190">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="9fef9-191">Étape 2 : Définir le service de fabrique WCF pour l'objet de session</span><span class="sxs-lookup"><span data-stu-id="9fef9-191">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="9fef9-192">Le service qui crée l'objet de session doit être défini et implémenté.</span><span class="sxs-lookup"><span data-stu-id="9fef9-192">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="9fef9-193">Le code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="9fef9-193">The following code shows how to do this.</span></span> <span data-ttu-id="9fef9-194">Ce code crée un autre service WCF qui retourne un objet <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="9fef9-194">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="9fef9-195">Il s'agit d'une forme sérialisable d'un point de terminaison qui peut être utilisée pour créer l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-195">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="9fef9-196">Voici l’implémentation de ce service.</span><span class="sxs-lookup"><span data-stu-id="9fef9-196">The following is the implementation of this service.</span></span> <span data-ttu-id="9fef9-197">Cette implémentation gère une fabrique de canaux singleton pour créer des objets de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-197">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="9fef9-198">Quand `GetInstanceAddress` est appelé, il crée un canal et un objet <xref:System.ServiceModel.EndpointAddress10> qui pointe vers l'adresse distante associée à ce canal.</span><span class="sxs-lookup"><span data-stu-id="9fef9-198">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="9fef9-199"><xref:System.ServiceModel.EndpointAddress10> est un type de données qui peut être renvoyé au client par valeur.</span><span class="sxs-lookup"><span data-stu-id="9fef9-199"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="9fef9-200">Étape 3 : Configurer et démarrer les services WCF</span><span class="sxs-lookup"><span data-stu-id="9fef9-200">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="9fef9-201">Pour héberger ces services, vous devrez effectuer les ajouts suivants au fichier de configuration du serveur (web.config).</span><span class="sxs-lookup"><span data-stu-id="9fef9-201">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="9fef9-202">Ajoutez une section `<client>` qui décrive le point de terminaison de l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-202">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="9fef9-203">Dans ce scénario, le serveur agit comme un client et doit être configuré pour rendre ceci possible.</span><span class="sxs-lookup"><span data-stu-id="9fef9-203">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="9fef9-204">Dans la section `<services>`, déclarez les points de terminaison de service pour la fabrique et l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-204">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="9fef9-205">Cela permet au client de communiquer avec les points de terminaison du service, d'acquérir <xref:System.ServiceModel.EndpointAddress10> et de créer le canal de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-205">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="9fef9-206">Voici un exemple de fichier de configuration avec ces paramètres :</span><span class="sxs-lookup"><span data-stu-id="9fef9-206">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="9fef9-207">Ajoutez les lignes suivantes à une application console pour auto-héberger le service, puis démarrez l'application.</span><span class="sxs-lookup"><span data-stu-id="9fef9-207">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="9fef9-208">Étape 4 : Configurer le client et appeler le service</span><span class="sxs-lookup"><span data-stu-id="9fef9-208">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="9fef9-209">Configurez le client pour communiquer avec les services WCF en ajoutant les entrées suivantes dans le fichier de configuration d'application du projet (app.config).</span><span class="sxs-lookup"><span data-stu-id="9fef9-209">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="9fef9-210">Pour appeler le service, ajoutez le code au client qui servira à effectuer ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9fef9-210">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="9fef9-211">Créer un canal vers le service `ISessionBoundFactory`.</span><span class="sxs-lookup"><span data-stu-id="9fef9-211">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="9fef9-212">Utiliser le canal pour appeler le service `ISessionBoundFactory` et obtenir un objet <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="9fef9-212">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="9fef9-213">Utiliser <xref:System.ServiceModel.EndpointAddress10> pour créer un canal et obtenir un objet de session.</span><span class="sxs-lookup"><span data-stu-id="9fef9-213">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="9fef9-214">Appeler les méthodes `SetCurrentValue` et `GetCurrentValue` pour montrer que la même instance d'objet est utilisée pour plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="9fef9-214">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9fef9-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fef9-215">See also</span></span>

- [<span data-ttu-id="9fef9-216">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="9fef9-216">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="9fef9-217">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="9fef9-217">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="9fef9-218">Génération de clients</span><span class="sxs-lookup"><span data-stu-id="9fef9-218">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="9fef9-219">Services duplex</span><span class="sxs-lookup"><span data-stu-id="9fef9-219">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
