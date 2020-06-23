---
title: Migration de .NET Remoting vers WCF
description: Découvrez comment migrer une application qui utilise .NET Remoting pour utiliser WCF. Vous pouvez effectuer plusieurs scénarios de communication à distance courants dans WCF.
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: f6f526db09806008314980b71233b208d25359fc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246153"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="a8e0b-104">Migration de .NET Remoting vers WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-104">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="a8e0b-105">Cet article décrit comment migrer une application .NET Remoting vers Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-105">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a8e0b-106">Il compare d'abord les concepts similaires entre ces deux produits, puis explique comment transposer plusieurs scénarios Remoting courants dans WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-106">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="a8e0b-107">.NET Remoting est un produit hérité qui est uniquement pris en charge à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-107">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="a8e0b-108">Il n'est pas sécurisé dans les environnements de confiance mixte en raison de son incapacité à préserver les niveaux de confiance distincts entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-108">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="a8e0b-109">Par exemple, vous ne devez jamais exposer un point de terminaison .NET Remoting à Internet ou à des clients non approuvés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-109">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="a8e0b-110">Nous vous recommandons de migrer les applications Remoting existantes vers des technologies plus récentes qui offrent davantage de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-110">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="a8e0b-111">Si l'application utilise uniquement le protocole HTTP et qu'elle repose sur une conception RESTful, nous recommandons l'API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-111">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="a8e0b-112">Pour plus d'informations, consultez l'API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-112">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="a8e0b-113">Si l'application est basée sur SOAP ou qu'elle nécessite des protocoles non-HTTP (comme TCP), nous recommandons WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-113">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="a8e0b-114">Comparaison de .NET Remoting à WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-114">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="a8e0b-115">Cette section compare les blocs de construction de base de .NET Remoting à leurs équivalents WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-115">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="a8e0b-116">Nous utiliserons ces blocs de construction ultérieurement pour créer des scénarios client-serveur courants dans WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-116">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="a8e0b-117">Le graphique suivant résume les similitudes principales et les différences entre .NET Remoting et WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-117">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="a8e0b-118">.NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-118">.NET Remoting</span></span>|<span data-ttu-id="a8e0b-119">WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-119">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="a8e0b-120">Type de serveur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-120">Server type</span></span>|<span data-ttu-id="a8e0b-121">Sous-classe MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="a8e0b-121">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="a8e0b-122">Marquer avec l'attribut [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="a8e0b-122">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="a8e0b-123">Opérations de service</span><span class="sxs-lookup"><span data-stu-id="a8e0b-123">Service operations</span></span>|<span data-ttu-id="a8e0b-124">Méthodes publiques sur le type de serveur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-124">Public methods on server type</span></span>|<span data-ttu-id="a8e0b-125">Marquer avec l'attribut [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="a8e0b-125">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="a8e0b-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="a8e0b-126">Serialization</span></span>|<span data-ttu-id="a8e0b-127">ISerializable ou [Serializable]</span><span class="sxs-lookup"><span data-stu-id="a8e0b-127">ISerializable or [Serializable]</span></span>|<span data-ttu-id="a8e0b-128">DataContractSerializer ou XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="a8e0b-128">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="a8e0b-129">Objets passés</span><span class="sxs-lookup"><span data-stu-id="a8e0b-129">Objects passed</span></span>|<span data-ttu-id="a8e0b-130">Par valeur ou par référence</span><span class="sxs-lookup"><span data-stu-id="a8e0b-130">By-value or by-reference</span></span>|<span data-ttu-id="a8e0b-131">Par valeur uniquement</span><span class="sxs-lookup"><span data-stu-id="a8e0b-131">By-value only</span></span>|  
|<span data-ttu-id="a8e0b-132">Erreurs/exceptions</span><span class="sxs-lookup"><span data-stu-id="a8e0b-132">Errors/exceptions</span></span>|<span data-ttu-id="a8e0b-133">Toute exception sérialisable</span><span class="sxs-lookup"><span data-stu-id="a8e0b-133">Any serializable exception</span></span>|<span data-ttu-id="a8e0b-134">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="a8e0b-134">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="a8e0b-135">Objets proxy clients</span><span class="sxs-lookup"><span data-stu-id="a8e0b-135">Client proxy objects</span></span>|<span data-ttu-id="a8e0b-136">Proxys transparents fortement typés créés automatiquement à partir de MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="a8e0b-136">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="a8e0b-137">Les proxys fortement typés sont générés à la demande à l’aide de ChannelFactory\<TChannel></span><span class="sxs-lookup"><span data-stu-id="a8e0b-137">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="a8e0b-138">Plateforme requise</span><span class="sxs-lookup"><span data-stu-id="a8e0b-138">Platform required</span></span>|<span data-ttu-id="a8e0b-139">Le client et le serveur doivent utiliser un système d'exploitation Microsoft et .NET</span><span class="sxs-lookup"><span data-stu-id="a8e0b-139">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="a8e0b-140">Système multiplateforme</span><span class="sxs-lookup"><span data-stu-id="a8e0b-140">Cross-platform</span></span>|  
|<span data-ttu-id="a8e0b-141">Format de message</span><span class="sxs-lookup"><span data-stu-id="a8e0b-141">Message format</span></span>|<span data-ttu-id="a8e0b-142">Private</span><span class="sxs-lookup"><span data-stu-id="a8e0b-142">Private</span></span>|<span data-ttu-id="a8e0b-143">Normalisé (SOAP, WS-\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="a8e0b-143">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="a8e0b-144">Comparaison de l'implémentation serveur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-144">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="a8e0b-145">Création d'un serveur dans .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-145">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="a8e0b-146">Les types de serveur .NET Remoting doivent dériver de MarshalByRefObject et définir des méthodes que le client peut appeler, comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-146">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a8e0b-147">Les méthodes publiques de ce type de serveur constituent le contrat public à disposition des clients.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-147">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="a8e0b-148">Il n'y a pas de séparation entre l'interface publique du serveur et son implémentation : un seul type gère les deux.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-148">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="a8e0b-149">Une fois le type de serveur défini, il peut être mis à disposition des clients, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-149">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-150">Vous pouvez mettre à disposition le type Remoting en tant que serveur de plusieurs façons, notamment à l'aide de fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-150">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="a8e0b-151">Il s'agit là d'un exemple parmi d'autres.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-151">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="a8e0b-152">Création d'un serveur dans WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-152">Creating a Server in WCF</span></span>  
 <span data-ttu-id="a8e0b-153">L'étape équivalente dans WCF implique la création de deux types : le « contrat de service » public et l'implémentation concrète.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-153">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="a8e0b-154">Le premier type est déclaré en tant qu'interface marquée avec [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-154">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="a8e0b-155">Les méthodes à disposition des clients sont marquées avec [OperationContract] :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-155">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a8e0b-156">L'implémentation du serveur est définie dans une classe concrète distincte, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-156">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a8e0b-157">Une fois ces types définis, le serveur WCF peut être mis à disposition des clients, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-157">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="a8e0b-158">TCP est utilisé dans les deux exemples pour qu'ils soient les plus semblables possible.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-158">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="a8e0b-159">Consultez les procédures pas à pas des scénarios figurant plus loin dans cette rubrique pour obtenir des exemples d'utilisation du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-159">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="a8e0b-160">Vous pouvez configurer et héberger des services WCF de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-160">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="a8e0b-161">Cet exemple, qui illustre ce que l'on appelle l'auto-hébergement, n'est qu'un exemple parmi d'autres.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-161">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="a8e0b-162">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-162">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8e0b-163">Guide pratique pour définir un contrat de service</span><span class="sxs-lookup"><span data-stu-id="a8e0b-163">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="a8e0b-164">Configuration des services à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a8e0b-164">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="a8e0b-165">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="a8e0b-165">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="a8e0b-166">Comparaison de l'implémentation client</span><span class="sxs-lookup"><span data-stu-id="a8e0b-166">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="a8e0b-167">Création d'un client dans .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-167">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="a8e0b-168">Une fois un objet serveur .NET Remoting mis à disposition, il peut être consommé par des clients, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-168">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="a8e0b-169">L'instance de RemotingServer retournée à partir d'Activator.GetObject() est désignée sous le terme de « proxy transparent ».</span><span class="sxs-lookup"><span data-stu-id="a8e0b-169">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="a8e0b-170">Elle implémente l'API publique pour le type RemotingServer sur le client, mais toutes les méthodes appellent l'objet serveur en cours d'exécution dans un ordinateur ou un processus différent.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-170">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="a8e0b-171">Création d'un client dans WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-171">Creating a Client in WCF</span></span>  
 <span data-ttu-id="a8e0b-172">L'étape équivalente dans WCF implique l'utilisation d'une fabrique de canaux pour créer explicitement le proxy.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-172">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="a8e0b-173">Comme dans Remoting, l'objet proxy peut être utilisé pour appeler des opérations sur le serveur, ce qu'illustre l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-173">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-174">Cet exemple montre la programmation au niveau du canal, car elle présente plus de similitudes avec l'exemple Remoting.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-174">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="a8e0b-175">L’approche **Ajouter une référence de service** dans Visual Studio, qui génère du code pour simplifier la programmation du client, est également disponible.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-175">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="a8e0b-176">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-176">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8e0b-177">Programmation du client au niveau du canal</span><span class="sxs-lookup"><span data-stu-id="a8e0b-177">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="a8e0b-178">Comment : ajouter, mettre à jour ou supprimer une référence de service</span><span class="sxs-lookup"><span data-stu-id="a8e0b-178">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="a8e0b-179">Utilisation de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="a8e0b-179">Serialization Usage</span></span>  
 <span data-ttu-id="a8e0b-180">Bien que .NET Remoting et WCF utilisent tous deux la sérialisation pour envoyer des objets entre le client et le serveur, il existe des différences importantes :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-180">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="a8e0b-181">Les conventions et sérialiseurs utilisés pour indiquer les éléments à sérialiser ne sont pas les mêmes.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-181">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="a8e0b-182">.NET Remoting prend en charge la sérialisation « par référence ». Celle-ci permet d'accéder à une méthode ou à une propriété située sur une couche et d'exécuter du code sur l'autre couche, au-delà des limites de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-182">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="a8e0b-183">Cette fonctionnalité présente des failles de sécurité. C'est l'une des principales raisons pour lesquelles les points de terminaison Remoting ne doivent jamais être exposés à des clients non approuvés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-183">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="a8e0b-184">La sérialisation utilisée par Remoting fonctionne par exclusion (les éléments à ne pas sérialiser sont exclus explicitement), tandis que la sérialisation WCF fonctionne par inclusion (les éléments à sérialiser sont marqués explicitement).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-184">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="a8e0b-185">Sérialisation dans .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-185">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="a8e0b-186">.NET Remoting prend en charge deux méthodes pour sérialiser et désérialiser des objets entre le client et le serveur :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-186">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="a8e0b-187">*Par valeur* : les valeurs de l’objet sont sérialisées à travers les limites de niveau, et une nouvelle instance de cet objet est créée sur l’autre couche.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-187">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="a8e0b-188">Tous les appels aux méthodes ou aux propriétés de cette nouvelle instance s'exécutent uniquement au niveau local et n'affectent pas la couche ou l'objet d'origine.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-188">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="a8e0b-189">*Par référence* : une « référence d’objet » spéciale est sérialisée à travers les limites de niveau.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-189">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="a8e0b-190">Quand une couche interagit avec les méthodes ou les propriétés de cet objet, elle communique avec l'objet d'origine situé sur la couche d'origine.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-190">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="a8e0b-191">Les objets par référence peuvent circuler dans les deux sens : du serveur au client ou du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-191">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="a8e0b-192">Les types par valeur dans Remoting sont marqués avec l'attribut [Serializable] ou implémentent ISerializable, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-192">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a8e0b-193">Les types par référence dérivent de la classe MarshalByRefObject, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-193">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a8e0b-194">Il est extrêmement important de comprendre les implications des objets par référence de Remoting.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-194">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="a8e0b-195">Si une couche (client ou serveur) envoie un objet par référence à l'autre couche, tous les appels de méthode s'exécutent sur la couche qui possède l'objet.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-195">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="a8e0b-196">Par exemple, un client appelant des méthodes sur un objet par référence retourné par le serveur exécute le code sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-196">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="a8e0b-197">De même, un serveur appelant des méthodes sur un objet par référence fourni par le client exécute le code sur le client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-197">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="a8e0b-198">Pour cette raison, il est recommandé d'utiliser .NET Remoting uniquement dans des environnements entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-198">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="a8e0b-199">Le fait d'exposer un point de terminaison .NET Remoting public à des clients non approuvés rend un serveur Remoting vulnérable aux attaques.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-199">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="a8e0b-200">Sérialisation dans WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-200">Serialization in WCF</span></span>  
 <span data-ttu-id="a8e0b-201">WCF prend uniquement en charge la sérialisation par valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-201">WCF supports only by-value serialization.</span></span> <span data-ttu-id="a8e0b-202">La méthode la plus couramment employée pour définir un type à échanger entre le client et le serveur est semblable à celle présentée dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-202">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-203">L'attribut [DataContract] identifie ce type comme pouvant être sérialisé et désérialisé entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-203">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="a8e0b-204">L'attribut [DataMember] identifie les propriétés ou les champs individuels à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-204">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="a8e0b-205">Quand WCF envoie un objet d'une couche à l'autre, il sérialise uniquement les valeurs et crée une instance de l'objet sur l'autre couche.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-205">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="a8e0b-206">Les interactions avec les valeurs de l'objet s'effectuent uniquement au niveau local ; contrairement aux objets par référence .NET Remoting, aucune communication n'a lieu avec l'autre couche.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-206">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="a8e0b-207">Pour plus d’informations, consultez [sérialisation et désérialisation](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-207">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="a8e0b-208">Capacités de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="a8e0b-208">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="a8e0b-209">Exceptions dans .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-209">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="a8e0b-210">Les exceptions levées par un serveur Remoting sont sérialisées, envoyées au client et levées localement sur le client comme n'importe quelle autre exception.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-210">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="a8e0b-211">Vous pouvez créer des exceptions personnalisées en définissant une sous-classe du type Exception et en la marquant avec [Serializable].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-211">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="a8e0b-212">La plupart des exceptions d'infrastructure étant déjà marquées de cette manière, elles peuvent être levées par le serveur, sérialisées et levées à nouveau sur le client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-212">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="a8e0b-213">Bien que cette conception présente des avantages lors du développement, il est possible que des informations côté serveur soient transmises par inadvertance au client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-213">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="a8e0b-214">C'est l'une des nombreuses raisons pour lesquelles Remoting doit uniquement être utilisé dans des environnements entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-214">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="a8e0b-215">Exceptions et erreurs dans WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-215">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="a8e0b-216">Pour éviter la divulgation inopportune d'informations, WCF n'autorise pas le serveur à retourner des types d'exceptions arbitraires au client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-216">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="a8e0b-217">Si une opération de service lève une exception inattendue, un FaultException à usage général est levé sur le client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-217">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="a8e0b-218">Bien que cette exception ne comprenne pas d'informations sur la raison ou l'emplacement du problème, elle suffit à certaines applications.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-218">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="a8e0b-219">Pour communiquer des informations d'erreur plus détaillées au client, les applications doivent définir un contrat d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-219">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="a8e0b-220">Pour cela, vous devez d'abord créer un type [DataContract] qui contiendra les informations d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-220">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-221">Spécifiez le contrat d'erreur à utiliser pour chaque opération de service.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-221">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a8e0b-222">Le serveur signale les conditions d'erreur en levant un FaultException.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-222">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="a8e0b-223">Chaque fois que le client effectue une demande au serveur, il peut intercepter les erreurs comme des exceptions normales.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-223">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-224">Pour plus d'informations sur les contrats d'erreur, consultez <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-224">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="a8e0b-225">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="a8e0b-225">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="a8e0b-226">Sécurité dans .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8e0b-226">Security in .NET Remoting</span></span>  
 <span data-ttu-id="a8e0b-227">Certains canaux .NET Remoting prennent en charge des fonctionnalités de sécurité telles que l'authentification et le chiffrement au niveau de la couche du canal (IPC et TCP).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-227">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="a8e0b-228">Le canal HTTP s'appuie sur les services Internet (IIS) pour procéder à l'authentification et au chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-228">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="a8e0b-229">Toutefois, vous devez considérer .NET Remoting comme un protocole de communication non sécurisé et l'utiliser uniquement dans des environnements entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-229">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="a8e0b-230">N'exposez jamais un point de terminaison Remoting public à Internet ou à des clients non approuvés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-230">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="a8e0b-231">Sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-231">Security in WCF</span></span>  
 <span data-ttu-id="a8e0b-232">WCF a été conçu dans une optique de sécurité, en partie pour résoudre les types de vulnérabilités associées à .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-232">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="a8e0b-233">Outre la sécurité au niveau du transport et des messages, WCF offre de nombreuses options en ce qui concerne l'authentification, l'autorisation, le chiffrement, etc.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-233">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="a8e0b-234">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-234">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8e0b-235">Sécurité</span><span class="sxs-lookup"><span data-stu-id="a8e0b-235">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="a8e0b-236">Guide de sécurité WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-236">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="a8e0b-237">Migration vers WCF</span><span class="sxs-lookup"><span data-stu-id="a8e0b-237">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="a8e0b-238">Pourquoi effectuer la migration de Remoting vers WCF ?</span><span class="sxs-lookup"><span data-stu-id="a8e0b-238">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="a8e0b-239">**.NET Remoting est un produit hérité.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-239">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="a8e0b-240">Comme décrit dans [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), il est considéré comme un produit hérité et n’est pas recommandé pour un nouveau développement.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-240">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="a8e0b-241">Il est recommandé d'utiliser WCF ou l'API Web ASP.NET pour les applications nouvelles et existantes.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-241">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="a8e0b-242">**WCF utilise des normes multiplateformes.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-242">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="a8e0b-243">Conçu pour mettre en avant l'interopérabilité multiplateforme, WCF prend en charge de nombreuses normes (SOAP, WS-Security, WS-Trust, etc.).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-243">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="a8e0b-244">Un service WCF peut interagir avec des clients en cours d'exécution sur des systèmes d'exploitation autres que Windows.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-244">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="a8e0b-245">La communication à distance a été conçue principalement pour les environnements dans lesquels les applications serveur et clientes s’exécutent à l’aide de .NET Framework sur un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-245">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="a8e0b-246">**WCF intègre des mesures de sécurité.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-246">**WCF has built-in security.**</span></span> <span data-ttu-id="a8e0b-247">WCF a été conçu en tenant compte de la sécurité et offre de nombreuses options pour l’authentification, la sécurité au niveau du transport, la sécurité au niveau des messages, etc. La communication à distance a été conçue pour faciliter l’interopérabilité des applications, mais elle n’a pas été conçue pour être sécurisée dans des environnements non approuvés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-247">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="a8e0b-248">De par sa conception, WCF fonctionne dans les environnements approuvés et non approuvés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-248">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="a8e0b-249">Recommandations en matière de migration</span><span class="sxs-lookup"><span data-stu-id="a8e0b-249">Migration Recommendations</span></span>  
 <span data-ttu-id="a8e0b-250">Voici les étapes recommandées pour effectuer la migration de Remoting vers WCF :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-250">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="a8e0b-251">**Créer le contrat de service.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-251">**Create the service contract.**</span></span> <span data-ttu-id="a8e0b-252">Définissez vos types d'interface de service et marquez-les avec l'attribut [ServiceContract]. Marquez toutes les méthodes que les clients peuvent appeler avec [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-252">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="a8e0b-253">**Créez le contrat de données.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-253">**Create the data contract.**</span></span> <span data-ttu-id="a8e0b-254">Définissez les types de données échangées entre le serveur et le client, puis marquez-les avec l'attribut [DataContract].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-254">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="a8e0b-255">Marquez tous les champs et propriétés que le client pourra utiliser avec [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-255">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="a8e0b-256">**Créer le contrat d'erreur (facultatif).**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-256">**Create the fault contract (optional).**</span></span> <span data-ttu-id="a8e0b-257">Créez les types échangés entre le client et le serveur en cas d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-257">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="a8e0b-258">Marquez ces types avec [DataContract] et [DataMember] pour les rendre sérialisables.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-258">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="a8e0b-259">Concernant les opérations de service marquées avec [OperationContract], marquez-les aussi avec [FaultContract] pour indiquer les erreurs qu'elles peuvent retourner.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-259">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="a8e0b-260">**Configurer et héberger le service.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-260">**Configure and host the service.**</span></span> <span data-ttu-id="a8e0b-261">Une fois le contrat de service créé, l’étape suivante consiste à configurer une liaison pour exposer le service à un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-261">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="a8e0b-262">Pour plus d’informations, consultez [points de terminaison : adresses, liaisons et contrats](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-262">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="a8e0b-263">À l'issue de la migration d'une application Remoting vers WCF, il est toujours important de supprimer les dépendances à .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-263">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="a8e0b-264">Cela permet de s'assurer que toutes les vulnérabilités de Remoting sont supprimées de l'application.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-264">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="a8e0b-265">Notamment :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-265">These steps include the following:</span></span>  
  
- <span data-ttu-id="a8e0b-266">**Cesser d'utiliser MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-266">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="a8e0b-267">Le type MarshalByRefObject concerne uniquement Remoting et n’est pas utilisé par WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-267">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="a8e0b-268">Les types d’applications qui définissent des sous-classes de MarshalByRefObject doivent être supprimés ou modifiés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-268">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="a8e0b-269">**Cesser d'utiliser [Serializable] et ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-269">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="a8e0b-270">Conçus à l'origine pour sérialiser les types dans les environnements fiables, l'attribut [Serializable] et l'interface ISerializable sont utilisés par Remoting.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-270">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="a8e0b-271">La sérialisation WCF s'appuie sur les types marqués avec [DataContract] et [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-271">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="a8e0b-272">Les types de données utilisés par une application doivent être modifiés afin d'utiliser [DataContract] et non l'interface ISerializable ou [Serializable].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-272">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="a8e0b-273">Scénarios de migration</span><span class="sxs-lookup"><span data-stu-id="a8e0b-273">Migration Scenarios</span></span>  
 <span data-ttu-id="a8e0b-274">Nous allons à présent voir comment transposer des scénarios Remoting courants suivants dans WCF :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-274">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="a8e0b-275">Le serveur retourne un objet par valeur au client</span><span class="sxs-lookup"><span data-stu-id="a8e0b-275">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="a8e0b-276">Le serveur retourne un objet par référence au client</span><span class="sxs-lookup"><span data-stu-id="a8e0b-276">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="a8e0b-277">Le client envoie un objet par valeur au serveur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-277">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8e0b-278">L'envoi d'un objet par référence du client vers le serveur n'est pas autorisé dans WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-278">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="a8e0b-279">Quand vous lisez ces scénarios, tenez compte du fait que nos interfaces de planning de référence pour .NET Remoting ressemblent à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-279">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="a8e0b-280">L'implémentation de .NET Remoting n'est pas importante ici, car notre objectif est de montrer comment utiliser WCF pour implémenter des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-280">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="a8e0b-281">Scénario 1 : service retournant un objet par valeur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-281">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="a8e0b-282">Ce scénario présente un serveur qui retourne un objet par valeur au client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-282">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="a8e0b-283">WCF retourne toujours les objets du serveur par valeur. Les étapes suivantes décrivent donc la création d'un service WCF normal.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-283">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="a8e0b-284">Commencez par définir une interface publique pour le service WCF et marquez-la avec l'attribut [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-284">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="a8e0b-285">[OperationContract] nous permet d'identifier les méthodes côté serveur qui seront appelées par notre client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-285">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="a8e0b-286">L'étape suivante consiste à créer le contrat de données pour ce service.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-286">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="a8e0b-287">Pour cela, nous créons des classes (et non des interfaces) marquées avec l'attribut [DataContract].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-287">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="a8e0b-288">Les propriétés ou champs individuels qui doivent être visibles au client et au serveur sont marqués avec [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-288">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="a8e0b-289">Pour autoriser les types dérivés, nous devons les identifier à l'aide de l'attribut [KnownType].</span><span class="sxs-lookup"><span data-stu-id="a8e0b-289">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="a8e0b-290">Les seuls types dont WCF autorise la sérialisation ou la désérialisation pour ce service sont ceux contenus dans l'interface de service et ces « types connus ».</span><span class="sxs-lookup"><span data-stu-id="a8e0b-290">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="a8e0b-291">Toute tentative visant à échanger un autre type ne figurant pas dans cette liste sera rejetée.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-291">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="a8e0b-292">Ensuite, nous devons fournir l'implémentation de l'interface de service.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-292">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="a8e0b-293">Pour exécuter le service WCF, nous devons déclarer un point de terminaison qui expose cette interface de service à une URL spécifique à l'aide d'une liaison WCF spécifique.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-293">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="a8e0b-294">Pour cela, il suffit généralement d'ajouter les sections suivantes au fichier web.config du projet serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-294">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="a8e0b-295">Le service WCF peut ensuite être démarré à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-295">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="a8e0b-296">Quand ServiceHost démarre, il utilise le fichier web.config pour établir le contrat, la liaison et le point de terminaison appropriés.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-296">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="a8e0b-297">Pour plus d’informations sur les fichiers de configuration, consultez [Configuration des services à l’aide de fichiers de configuration](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-297">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="a8e0b-298">On parle d'auto-hébergement pour désigner ce type de démarrage du serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-298">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="a8e0b-299">Pour en savoir plus sur les autres options d’hébergement des services WCF, consultez [services d’hébergement](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-299">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="a8e0b-300">Le fichier app.config du projet client doit déclarer les informations de liaison correspondante pour le point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-300">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="a8e0b-301">La méthode la plus simple pour effectuer cette opération dans Visual Studio consiste à utiliser **Ajouter une référence de service**, qui mettra à jour automatiquement le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-301">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="a8e0b-302">Vous pouvez également ajouter manuellement ces mêmes modifications.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-302">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="a8e0b-303">Pour plus d’informations sur l’utilisation de **Ajouter une référence de service**, consultez [Comment : ajouter, mettre à jour ou supprimer une référence de service](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-303">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="a8e0b-304">Nous pouvons maintenant appeler le service WCF à partir du client.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-304">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="a8e0b-305">Pour cela, nous créons une fabrique de canaux pour ce service, nous demandons un canal, puis nous appelons directement la méthode que nous voulons sur ce canal.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-305">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="a8e0b-306">Si nous pouvons procéder de la sorte, c'est parce que le canal implémente l'interface du service et qu'il gère pour nous la logique sous-jacente des demandes/réponses.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-306">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="a8e0b-307">La valeur de retour de cet appel de méthode est la copie désérialisée de la réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-307">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="a8e0b-308">Les objets retournés par WCF du serveur au client sont toujours par valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-308">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="a8e0b-309">Les objets sont des copies désérialisées des données envoyées par le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-309">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="a8e0b-310">Le client peut appeler des méthodes sur ces copies locales sans aucun risque d'appeler le code serveur via des rappels.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-310">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="a8e0b-311">Scénario 2 : serveur retournant un objet par référence</span><span class="sxs-lookup"><span data-stu-id="a8e0b-311">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="a8e0b-312">Ce scénario présente un serveur qui fournit un objet au client par référence.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-312">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="a8e0b-313">Dans .NET Remoting, ceci est géré automatiquement pour n’importe quel type dérivé de MarshalByRefObject, qui est sérialisé par référence.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-313">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="a8e0b-314">Autoriser plusieurs clients à avoir des objets côté serveur de session indépendants est un exemple de ce scénario.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-314">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="a8e0b-315">Comme mentionné précédemment, les objets retournés par un service WCF sont toujours des objets par valeur. Il n'y a donc pas d'équivalent direct à un objet par référence, mais vous pouvez obtenir des résultats semblables à la sémantique par référence en utilisant un objet <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-315">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="a8e0b-316">Il s'agit d'un objet par valeur sérialisable qui peut être utilisé par le client pour obtenir un objet par référence de session sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-316">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="a8e0b-317">Cela permet la prise en charge de plusieurs clients avec des objets côté serveur de session indépendants.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-317">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="a8e0b-318">Tout d'abord, nous devons définir un contrat de service WCF qui correspond à l'objet de session proprement dit.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-318">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="a8e0b-319">Notez que l'objet de session est marqué avec [ServiceContract], ce qui en fait une interface de service WCF normale.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-319">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="a8e0b-320">Le fait de définir la propriété SessionMode indique qu'il s'agit d'un service de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-320">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="a8e0b-321">Dans WCF, une session est une façon de mettre en corrélation plusieurs messages envoyés entre deux points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-321">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="a8e0b-322">Cela signifie qu'une fois qu'un client obtient une connexion à ce service, une session est établie entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-322">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="a8e0b-323">Le client utilisera une seule instance de l'objet côté serveur pour toutes ses interactions au sein de cette session unique.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-323">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="a8e0b-324">Nous devons ensuite fournir l'implémentation de l'interface du service.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-324">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="a8e0b-325">En spécifiant [ServiceBehavior] et en définissant InstanceContextMode, nous indiquons à WCF que nous souhaitons utiliser une instance unique de ce type pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-325">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="a8e0b-326">Nous devons à présent trouver le moyen d'obtenir une instance de cet objet de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-326">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="a8e0b-327">Pour cela, nous créons une autre interface de service WCF qui retourne un objet EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-327">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="a8e0b-328">Il s'agit d'une forme sérialisable d'un point de terminaison que le client peut utiliser pour créer l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-328">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="a8e0b-329">Puis nous implémentons ce service WCF :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-329">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="a8e0b-330">Cette implémentation gère une fabrique de canaux singleton pour créer des objets de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-330">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="a8e0b-331">Quand GetInstanceAddress() est appelé, il crée un canal et un objet EndpointAddress10 qui pointe vers l'adresse distante associée à ce canal.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-331">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="a8e0b-332">EndpointAddress10 est simplement un type de données qui peut être retourné au client par valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-332">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="a8e0b-333">Pour modifier le fichier de configuration du serveur, nous devons effectuer les deux tâches suivantes, comme le montre l'exemple ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-333">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="a8e0b-334">Déclarez une \<client> section qui décrit le point de terminaison de l’objet de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-334">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="a8e0b-335">Cette opération est nécessaire, car le serveur joue également le rôle de client dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-335">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="a8e0b-336">Déclarez les points de terminaison pour la fabrique et l'objet de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-336">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="a8e0b-337">Cette opération est nécessaire afin de permettre au client de communiquer avec les points de terminaison du service pour acquérir l'objet EndpointAddress10 et créer le canal de session.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-337">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="a8e0b-338">Ensuite, nous pouvons démarrer ces services :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-338">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="a8e0b-339">Nous configurons le client en déclarant ces mêmes points de terminaison dans le fichier app.config de son projet.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-339">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="a8e0b-340">Pour créer et utiliser cet objet de session, le client doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8e0b-340">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="a8e0b-341">Créer un canal jusqu'au service ISessionBoundFactory</span><span class="sxs-lookup"><span data-stu-id="a8e0b-341">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="a8e0b-342">Utiliser ce canal pour appeler ce service afin d'obtenir un objet EndpointAddress10</span><span class="sxs-lookup"><span data-stu-id="a8e0b-342">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="a8e0b-343">Utiliser l'objet EndpointAddress10 pour créer un canal et obtenir un objet de session</span><span class="sxs-lookup"><span data-stu-id="a8e0b-343">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="a8e0b-344">Interagir avec l'objet de session pour montrer qu'il s'agit de la même instance sur plusieurs appels</span><span class="sxs-lookup"><span data-stu-id="a8e0b-344">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="a8e0b-345">WCF retourne toujours les objets par valeur, mais il est possible de prendre en charge l'équivalent de la sémantique par référence en utilisant l'objet EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-345">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="a8e0b-346">Le client peut ainsi demander une instance de service WCF de session avec laquelle il peut ensuite interagir comme n'importe quel autre service WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-346">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="a8e0b-347">Scénario 3 : envoi par le client au serveur d'une instance par valeur</span><span class="sxs-lookup"><span data-stu-id="a8e0b-347">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="a8e0b-348">Ce scénario présente un client qui envoie une instance d'objet non primitif au serveur par valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-348">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="a8e0b-349">Étant donné que WCF envoie uniquement les objets par valeur, ce scénario illustre une utilisation normale de WCF.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-349">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="a8e0b-350">Utilisez le même service WCF que celui du scénario 1.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-350">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="a8e0b-351">Utilisez le client pour créer un objet par valeur (Customer), créez un canal pour communiquer avec le service ICustomerService, puis envoyez-lui l'objet.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-351">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="a8e0b-352">L'objet Customer est sérialisé, puis envoyé au service où il est désérialisé en nouvelle copie de cet objet.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-352">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a8e0b-353">Ce code illustre également l'envoi d'un type dérivé (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-353">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="a8e0b-354">L'interface de service attend un objet Customer, mais l'attribut [KnownType] sur la classe Customer indique que PremiumCustomer est également autorisé.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-354">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="a8e0b-355">Les tentatives de WCF de sérialisation ou de désérialisation de tout autre type via cette interface de service échouent.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-355">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="a8e0b-356">Dans WCF, les données sont normalement échangées par valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-356">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="a8e0b-357">Cela garantit que l'appel de méthodes sur l'un de ces objets de données s'exécute uniquement au niveau local (le code sur l'autre couche n'est pas appelé).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-357">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="a8e0b-358">Bien qu’il soit possible d' *obtenir des objets par référence renvoyés* par le serveur, il n’est pas possible pour un client de passer un objet par référence *au* serveur.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-358">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="a8e0b-359">Une conversation entre un client et un serveur peut être effectuée dans WCF à l'aide d'un service duplex.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-359">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="a8e0b-360">Pour plus d’informations, consultez [services duplex](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-360">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="a8e0b-361">Résumé</span><span class="sxs-lookup"><span data-stu-id="a8e0b-361">Summary</span></span>  
 <span data-ttu-id="a8e0b-362">.NET Remoting est une infrastructure de communication destinée à être utilisée uniquement dans des environnements entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-362">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="a8e0b-363">Il s'agit d'un produit hérité qui est uniquement pris en charge à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-363">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="a8e0b-364">Il ne doit pas être utilisé pour développer de nouvelles applications.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-364">It should not be used to build new applications.</span></span> <span data-ttu-id="a8e0b-365">À l'inverse, WCF a été conçu dans une optique de sécurité et est recommandé pour les applications nouvelles et existantes.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-365">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="a8e0b-366">Microsoft recommande de migrer les applications Remoting existantes vers WCF ou l'API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-366">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
