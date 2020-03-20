---
title: Sous-système approuvé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: b226eed9218207cde99add61ef1f3eb64b459009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184304"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="f2aef-102">Sous-système approuvé</span><span class="sxs-lookup"><span data-stu-id="f2aef-102">Trusted Subsystem</span></span>
<span data-ttu-id="f2aef-103">Un client accède à un ou plusieurs services Web distribués sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="f2aef-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="f2aef-104">Les services Web sont conçus afin que l'accès aux ressources supplémentaires (telles que les bases de données ou autres services Web) soit encapsulé dans la logique métier du service Web.</span><span class="sxs-lookup"><span data-stu-id="f2aef-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="f2aef-105">Ces ressources doivent être protégées contre tout accès non autorisé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="f2aef-106">L'illustration suivante présente un processus de sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="f2aef-107">![Sous-système de confiance](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="f2aef-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="f2aef-108">Les étapes suivantes décrivent le processus de sous-système approuvé tel qu'il est présenté :</span><span class="sxs-lookup"><span data-stu-id="f2aef-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="f2aef-109">Le client envoie une demande au sous-système approuvé, accompagnée des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="f2aef-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="f2aef-110">Le sous-système approuvé authentifie et autorise l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2aef-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="f2aef-111">Le sous-système approuvé envoie un message de demande à la ressource distante.</span><span class="sxs-lookup"><span data-stu-id="f2aef-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="f2aef-112">Cette demande est accompagnée des informations d'identification du sous-système approuvé (ou le compte de service sous lequel le processus de sous-système approuvé est exécuté).</span><span class="sxs-lookup"><span data-stu-id="f2aef-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="f2aef-113">La ressource principale authentifie et autorise le sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="f2aef-114">Elle traite ensuite la demande et envoie une réponse au sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="f2aef-115">Le sous-système approuvé traite la réponse et envoie sa propre réponse au client.</span><span class="sxs-lookup"><span data-stu-id="f2aef-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="f2aef-116">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="f2aef-116">Characteristic</span></span>|<span data-ttu-id="f2aef-117">Description</span><span class="sxs-lookup"><span data-stu-id="f2aef-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f2aef-118">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="f2aef-118">Security Mode</span></span>|<span data-ttu-id="f2aef-119">Message</span><span class="sxs-lookup"><span data-stu-id="f2aef-119">Message</span></span>|  
|<span data-ttu-id="f2aef-120">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f2aef-120">Interoperability</span></span>|<span data-ttu-id="f2aef-121">Windows Communication Foundation (WCF) uniquement.</span><span class="sxs-lookup"><span data-stu-id="f2aef-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="f2aef-122">Authentification (service)</span><span class="sxs-lookup"><span data-stu-id="f2aef-122">Authentication (service)</span></span>|<span data-ttu-id="f2aef-123">Le service de jeton de sécurité authentifie et autorise des clients.</span><span class="sxs-lookup"><span data-stu-id="f2aef-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="f2aef-124">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="f2aef-124">Authentication (client)</span></span>|<span data-ttu-id="f2aef-125">Le sous-système approuvé authentifie le client et la ressource authentifie le service du sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="f2aef-126">Intégrité</span><span class="sxs-lookup"><span data-stu-id="f2aef-126">Integrity</span></span>|<span data-ttu-id="f2aef-127">Oui</span><span class="sxs-lookup"><span data-stu-id="f2aef-127">Yes</span></span>|  
|<span data-ttu-id="f2aef-128">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="f2aef-128">Confidentiality</span></span>|<span data-ttu-id="f2aef-129">Oui</span><span class="sxs-lookup"><span data-stu-id="f2aef-129">Yes</span></span>|  
|<span data-ttu-id="f2aef-130">Transport</span><span class="sxs-lookup"><span data-stu-id="f2aef-130">Transport</span></span>|<span data-ttu-id="f2aef-131">HTTP entre client et le service du sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="f2aef-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="f2aef-132">NET.TCP entre le service du sous-système approuvé et la ressource (service principal).</span><span class="sxs-lookup"><span data-stu-id="f2aef-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="f2aef-133">Liaison</span><span class="sxs-lookup"><span data-stu-id="f2aef-133">Binding</span></span>|<span data-ttu-id="f2aef-134"><xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NetTcpBinding> [et \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f2aef-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="f2aef-135">Ressource (service principal)</span><span class="sxs-lookup"><span data-stu-id="f2aef-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="f2aef-136">Code</span><span class="sxs-lookup"><span data-stu-id="f2aef-136">Code</span></span>  
 <span data-ttu-id="f2aef-137">Le code suivant indique comment créer un point de terminaison de service pour la ressource, qui utilise la sécurité de transport sur le protocole de transport TCP.</span><span class="sxs-lookup"><span data-stu-id="f2aef-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="f2aef-138">Configuration</span><span class="sxs-lookup"><span data-stu-id="f2aef-138">Configuration</span></span>  
 <span data-ttu-id="f2aef-139">La configuration suivante configure le même point de terminaison en utilisant la configuration.</span><span class="sxs-lookup"><span data-stu-id="f2aef-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="f2aef-140">Sous-système approuvé</span><span class="sxs-lookup"><span data-stu-id="f2aef-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="f2aef-141">Code</span><span class="sxs-lookup"><span data-stu-id="f2aef-141">Code</span></span>  
 <span data-ttu-id="f2aef-142">Le code suivant indique comment créer un point de terminaison de service pour le sous-système approuvé qui utilise la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="f2aef-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="f2aef-143">Le code suivant affiche un service dans un sous-système approuvé qui communique avec un service principal en utilisant la sécurité de transport sur le protocole de transport TCP.</span><span class="sxs-lookup"><span data-stu-id="f2aef-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="f2aef-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="f2aef-144">Configuration</span></span>  
 <span data-ttu-id="f2aef-145">La configuration suivante configure le même point de terminaison en utilisant la configuration.</span><span class="sxs-lookup"><span data-stu-id="f2aef-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="f2aef-146">Notez les deux liaisons : l'une sécurise le service hébergé dans le sous-système approuvé et l'autre communique entre le sous-système approuvé et le service principal.</span><span class="sxs-lookup"><span data-stu-id="f2aef-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="f2aef-147">Client</span><span class="sxs-lookup"><span data-stu-id="f2aef-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="f2aef-148">Code</span><span class="sxs-lookup"><span data-stu-id="f2aef-148">Code</span></span>  
 <span data-ttu-id="f2aef-149">Le code suivant indique comment créer le client qui communique avec le sous-système approuvé en utilisant la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="f2aef-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="f2aef-150">Configuration</span><span class="sxs-lookup"><span data-stu-id="f2aef-150">Configuration</span></span>  
 <span data-ttu-id="f2aef-151">Le code suivant configure le client pour qu'il utilise la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="f2aef-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="f2aef-152">Le nom d'utilisateur et le mot de passe peuvent uniquement être spécifiés à l'aide du code (cela n'est pas configurable).</span><span class="sxs-lookup"><span data-stu-id="f2aef-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2aef-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2aef-153">See also</span></span>

- [<span data-ttu-id="f2aef-154">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="f2aef-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="f2aef-155">[Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f2aef-155">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
