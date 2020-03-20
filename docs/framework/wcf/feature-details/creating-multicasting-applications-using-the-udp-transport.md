---
title: Création d'applications multidiffusion en utilisant le transport UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 6825aaafe87ae362fd9266f7c7a82a36d054a69f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185252"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="41c8b-102">Création d'applications multidiffusion en utilisant le transport UDP</span><span class="sxs-lookup"><span data-stu-id="41c8b-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="41c8b-103">Les applications de multidiffusion envoient de petits messages à un grand nombre de destinataires à la fois sans établir de connexion point à point.</span><span class="sxs-lookup"><span data-stu-id="41c8b-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="41c8b-104">Ces applications mettent l'accent sur la vitesse par rapport à la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="41c8b-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="41c8b-105">En d'autres termes, il est plus important d'envoyer des données en temps voulu pour garantir que tout message spécifique est reçu.</span><span class="sxs-lookup"><span data-stu-id="41c8b-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="41c8b-106">WCF prend désormais en charge des applications de multidiffusion à l'aide de <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="41c8b-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="41c8b-107">Ce transport est utile dans les scénarios où un service doit envoyer de petits messages à plusieurs clients simultanément.</span><span class="sxs-lookup"><span data-stu-id="41c8b-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="41c8b-108">Une application de cotations boursières est un exemple de ce service.</span><span class="sxs-lookup"><span data-stu-id="41c8b-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="41c8b-109">Implémentation d'une application de multidiffusion</span><span class="sxs-lookup"><span data-stu-id="41c8b-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="41c8b-110">Pour implémenter une application de multidiffusion, définissez un contrat de service et pour chaque composant logiciel qui doit répondre aux messages de multidiffusion, implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="41c8b-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="41c8b-111">Par exemple, une application de cotations boursières peut définir un contrat de service :</span><span class="sxs-lookup"><span data-stu-id="41c8b-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="41c8b-112">Chaque application qui souhaite recevoir des messages de multidiffusion doit héberger un service qui expose cette interface.</span><span class="sxs-lookup"><span data-stu-id="41c8b-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="41c8b-113">Par exemple, voici un exemple de code qui montre comment recevoir des messages de multidiffusion :</span><span class="sxs-lookup"><span data-stu-id="41c8b-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="41c8b-114">L'application spécifie l'adresse UDP sur laquelle tous les services écouteront.</span><span class="sxs-lookup"><span data-stu-id="41c8b-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="41c8b-115">Un <xref:System.ServiceModel.ServiceHost> est créé et un point de terminaison de service est exposé à l'aide de <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="41c8b-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="41c8b-116"><xref:System.ServiceModel.ServiceHost> est ensuite ouvert et va commencer à écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="41c8b-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="41c8b-117">Dans ce type de scénario, il s'agit du client qui envoie en fait des messages de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="41c8b-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="41c8b-118">Chaque service qui écoute à l'adresse UDP appropriée recevra les messages de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="41c8b-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="41c8b-119">Voici un exemple d'un client qui envoie des messages de multidiffusion :</span><span class="sxs-lookup"><span data-stu-id="41c8b-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="41c8b-120">Ce code génère les informations boursières, puis utilise le contrat de service IStockTicker de façon à envoyer des messages de multidiffusion et appeler les services à l'écoute sur l'adresse UDP appropriée.</span><span class="sxs-lookup"><span data-stu-id="41c8b-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="41c8b-121">UDP et messagerie fiable</span><span class="sxs-lookup"><span data-stu-id="41c8b-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="41c8b-122">La liaison UDP ne prend pas en charge la messagerie fiable en raison de la nature légère du protocole UDP.</span><span class="sxs-lookup"><span data-stu-id="41c8b-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="41c8b-123">Si vous devez vérifier que les messages sont reçus par un point de terminaison distant, utilisez un transport qui prend en charge la messagerie fiable telle que HTTP ou TCP.</span><span class="sxs-lookup"><span data-stu-id="41c8b-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="41c8b-124">Pour plus d’informations sur la messagerie fiable voirhttps://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="41c8b-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="41c8b-125">Messagerie de multidiffusion bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="41c8b-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="41c8b-126">Alors que les messages de multidiffusion sont généralement unidirectionnels, UdpBinding prend en charge l'échange de messages de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="41c8b-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="41c8b-127">Les messages envoyés à l'aide du transport UDP contiennent une adresse d'expéditeur et de destinataire.</span><span class="sxs-lookup"><span data-stu-id="41c8b-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="41c8b-128">Il faut être prudent lors de l'utilisation de l'adresse de l'expéditeur, car elle peut être modifiée de manière malveillante en route.</span><span class="sxs-lookup"><span data-stu-id="41c8b-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="41c8b-129">L'adresse peut être vérifiée à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="41c8b-129">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="41c8b-130">Ce code contrôle le premier octet de l'adresse du destinataire pour voir si elle contient 0xE0, ce qui signifie que l'adresse est une adresse de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="41c8b-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="41c8b-131">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="41c8b-131">Security Considerations</span></span>  
 <span data-ttu-id="41c8b-132">Lors de l'écoute des messages de multidiffusion, un paquet ICMP est envoyé au routeur pour l'informer que vous écoutez sur l'adresse de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="41c8b-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="41c8b-133">Toute personne sur le sous-réseau local qui dispose des autorisations nécessaires peut écouter ces types de paquets et déterminer l'adresse de multidiffusion et le port sur lesquels vous écoutez.</span><span class="sxs-lookup"><span data-stu-id="41c8b-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="41c8b-134">N'utilisez pas l'adresse IP de l'expéditeur à des fins de sécurité.</span><span class="sxs-lookup"><span data-stu-id="41c8b-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="41c8b-135">Ces informations peuvent être usurpées et peuvent provoquer l'envoi de réponses à un ordinateur incorrect.</span><span class="sxs-lookup"><span data-stu-id="41c8b-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="41c8b-136">Une façon pour atténuer cette menace consiste à activer la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="41c8b-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="41c8b-137">Au niveau du réseau IPSec (Internet Protocol Security) et/ou NAP (Network Access Protection) peut également être utilisé.</span><span class="sxs-lookup"><span data-stu-id="41c8b-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
