---
title: Sécurité de transport avec l'authentification par certificat
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184331"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="6931a-102">Sécurité de transport avec l'authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="6931a-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="6931a-103">Cet article traite de l’utilisation des certificats X.509 pour l’authentification du serveur et du client lors de l’utilisation de la sécurité des transports.</span><span class="sxs-lookup"><span data-stu-id="6931a-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="6931a-104">Pour plus d’informations sur les certificats X.509, consultez [Certificats de clé publique X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="6931a-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="6931a-105">Les certificats doivent être délivrés par une autorité de certification, qui est souvent un émetteur tiers de certificats.</span><span class="sxs-lookup"><span data-stu-id="6931a-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="6931a-106">Dans un domaine Windows Server, les services de certificats Active Directory peuvent être utilisés pour émettre des certificats pour les ordinateurs clients figurant sur le domaine.</span><span class="sxs-lookup"><span data-stu-id="6931a-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="6931a-107">Dans ce scénario, le service est hébergé sous Internet Information Services (IIS) qui est configuré avec SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="6931a-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="6931a-108">Le service est configuré avec un certificat SSL (X.509) pour permettre aux clients de vérifier l'identité du serveur.</span><span class="sxs-lookup"><span data-stu-id="6931a-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="6931a-109">Le client est également configuré avec un certificat X.509 qui permet au service de vérifier l'identité du client.</span><span class="sxs-lookup"><span data-stu-id="6931a-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="6931a-110">Le certificat du serveur doit être approuvé par le client et le certificat du client doit être approuvé par le serveur.</span><span class="sxs-lookup"><span data-stu-id="6931a-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="6931a-111">La mécanique réelle de la façon dont le service et le client vérifie l’identité de l’autre est au-delà de la portée de cet article.</span><span class="sxs-lookup"><span data-stu-id="6931a-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="6931a-112">Pour plus d’informations, voir [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) sur Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="6931a-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="6931a-113">Ce scénario implémente un modèle de message de demande/réponse comme illustré dans le schéma suivant.</span><span class="sxs-lookup"><span data-stu-id="6931a-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="6931a-114">![Transfert sécurisé à l’aide de certificats](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="6931a-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="6931a-115">Pour plus d’informations sur l’utilisation d’un certificat avec un service, voir [Travailler avec des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) et [comment : Configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="6931a-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="6931a-116">Le tableau suivant décrit les différentes caractéristiques du scénario.</span><span class="sxs-lookup"><span data-stu-id="6931a-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="6931a-117">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="6931a-117">Characteristic</span></span>|<span data-ttu-id="6931a-118">Description</span><span class="sxs-lookup"><span data-stu-id="6931a-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6931a-119">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="6931a-119">Security Mode</span></span>|<span data-ttu-id="6931a-120">Transport</span><span class="sxs-lookup"><span data-stu-id="6931a-120">Transport</span></span>|  
|<span data-ttu-id="6931a-121">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6931a-121">Interoperability</span></span>|<span data-ttu-id="6931a-122">Avec les clients de service Web et les services existants.</span><span class="sxs-lookup"><span data-stu-id="6931a-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="6931a-123">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="6931a-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="6931a-124">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="6931a-124">Authentication (Client)</span></span>|<span data-ttu-id="6931a-125">Oui (à l’aide d’un certificat SSL)</span><span class="sxs-lookup"><span data-stu-id="6931a-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="6931a-126">Oui (à l'aide d'un certificat X.509)</span><span class="sxs-lookup"><span data-stu-id="6931a-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="6931a-127">Intégrité des données</span><span class="sxs-lookup"><span data-stu-id="6931a-127">Data Integrity</span></span>|<span data-ttu-id="6931a-128">Oui</span><span class="sxs-lookup"><span data-stu-id="6931a-128">Yes</span></span>|  
|<span data-ttu-id="6931a-129">Confidentialité des données</span><span class="sxs-lookup"><span data-stu-id="6931a-129">Data Confidentiality</span></span>|<span data-ttu-id="6931a-130">Oui</span><span class="sxs-lookup"><span data-stu-id="6931a-130">Yes</span></span>|  
|<span data-ttu-id="6931a-131">Transport</span><span class="sxs-lookup"><span data-stu-id="6931a-131">Transport</span></span>|<span data-ttu-id="6931a-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="6931a-132">HTTPS</span></span>|  
|<span data-ttu-id="6931a-133">Liaison</span><span class="sxs-lookup"><span data-stu-id="6931a-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="6931a-134">Configuration du service</span><span class="sxs-lookup"><span data-stu-id="6931a-134">Configure the Service</span></span>  
 <span data-ttu-id="6931a-135">Puisque le service dans ce scénario est hébergé sous IIS, il est configuré à l'aide d'un fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="6931a-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="6931a-136">La configuration Web suivante illustre comment configurer le <xref:System.ServiceModel.WSHttpBinding> pour utiliser la sécurité de transport et les informations d'identification du client X.509.</span><span class="sxs-lookup"><span data-stu-id="6931a-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="6931a-137">Configuration du client</span><span class="sxs-lookup"><span data-stu-id="6931a-137">Configure the Client</span></span>  
 <span data-ttu-id="6931a-138">Le client peut être configuré en code ou dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="6931a-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="6931a-139">L'exemple suivant indique comment configurer le client en code.</span><span class="sxs-lookup"><span data-stu-id="6931a-139">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="6931a-140">Vous pouvez aussi configurer le client dans un fichier app.config, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6931a-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6931a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6931a-141">See also</span></span>

- [<span data-ttu-id="6931a-142">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="6931a-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="6931a-143">[Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6931a-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
