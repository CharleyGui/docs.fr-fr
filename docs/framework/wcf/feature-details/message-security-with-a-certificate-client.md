---
title: Sécurité de message avec un client de certificat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 3660877194931c2be5b9b1c9aa54e2595701697f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184655"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="ba3e3-102">Sécurité de message avec un client de certificat</span><span class="sxs-lookup"><span data-stu-id="ba3e3-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="ba3e3-103">Le scénario suivant montre un client et un service de la Windows Communication Foundation (WCF) sécurisés en mode de sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="ba3e3-104">Le client et le service sont tous les deux authentifiés à l'aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="ba3e3-105">Pour plus d’informations, voir [La sécurité des applications distribuées](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="ba3e3-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Capture d’écran qui montre un client avec un certificat.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="ba3e3-107">Pour une demande d’exemple, consultez [le certificat de sécurité des messages](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ba3e3-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="ba3e3-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="ba3e3-108">Characteristic</span></span>|<span data-ttu-id="ba3e3-109">Description</span><span class="sxs-lookup"><span data-stu-id="ba3e3-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ba3e3-110">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="ba3e3-110">Security Mode</span></span>|<span data-ttu-id="ba3e3-111">Message</span><span class="sxs-lookup"><span data-stu-id="ba3e3-111">Message</span></span>|  
|<span data-ttu-id="ba3e3-112">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="ba3e3-112">Interoperability</span></span>|<span data-ttu-id="ba3e3-113">WCF seulement</span><span class="sxs-lookup"><span data-stu-id="ba3e3-113">WCF only</span></span>|  
|<span data-ttu-id="ba3e3-114">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="ba3e3-114">Authentication (Server)</span></span>|<span data-ttu-id="ba3e3-115">Utilisation de certificat de service</span><span class="sxs-lookup"><span data-stu-id="ba3e3-115">Using service certificate</span></span>|  
|<span data-ttu-id="ba3e3-116">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="ba3e3-116">Authentication (Client)</span></span>|<span data-ttu-id="ba3e3-117">Utilisation de certificat client</span><span class="sxs-lookup"><span data-stu-id="ba3e3-117">Using client certificate</span></span>|  
|<span data-ttu-id="ba3e3-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="ba3e3-118">Integrity</span></span>|<span data-ttu-id="ba3e3-119">Oui</span><span class="sxs-lookup"><span data-stu-id="ba3e3-119">Yes</span></span>|  
|<span data-ttu-id="ba3e3-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="ba3e3-120">Confidentiality</span></span>|<span data-ttu-id="ba3e3-121">Oui</span><span class="sxs-lookup"><span data-stu-id="ba3e3-121">Yes</span></span>|  
|<span data-ttu-id="ba3e3-122">Transport</span><span class="sxs-lookup"><span data-stu-id="ba3e3-122">Transport</span></span>|<span data-ttu-id="ba3e3-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="ba3e3-123">HTTP</span></span>|  
|<span data-ttu-id="ba3e3-124">Liaison</span><span class="sxs-lookup"><span data-stu-id="ba3e3-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ba3e3-125">Service</span><span class="sxs-lookup"><span data-stu-id="ba3e3-125">Service</span></span>  
 <span data-ttu-id="ba3e3-126">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ba3e3-127">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba3e3-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="ba3e3-128">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ba3e3-129">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ba3e3-130">Code</span><span class="sxs-lookup"><span data-stu-id="ba3e3-130">Code</span></span>  
 <span data-ttu-id="ba3e3-131">Le code ci-dessous montre comment créer un point de terminaison de service qui utilise la sécurité de message pour établir un contexte sécurisé.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="ba3e3-132">Configuration</span><span class="sxs-lookup"><span data-stu-id="ba3e3-132">Configuration</span></span>  
 <span data-ttu-id="ba3e3-133">La configuration ci-dessous peut être utilisée à la place du code.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ba3e3-134">Client</span><span class="sxs-lookup"><span data-stu-id="ba3e3-134">Client</span></span>  
 <span data-ttu-id="ba3e3-135">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ba3e3-136">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba3e3-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="ba3e3-137">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="ba3e3-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="ba3e3-138">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ba3e3-139">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ba3e3-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ba3e3-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ba3e3-141">Code</span><span class="sxs-lookup"><span data-stu-id="ba3e3-141">Code</span></span>  
 <span data-ttu-id="ba3e3-142">Le code ci-dessous crée le client.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-142">The following code creates the client.</span></span> <span data-ttu-id="ba3e3-143">La liaison s’effectue avec la sécurité en mode de message et le type d’informations d’identification client a la valeur `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="ba3e3-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="ba3e3-144">Configuration</span></span>  
 <span data-ttu-id="ba3e3-145">La configuration ci-dessous spécifie le certificat client à l'aide d'un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="ba3e3-146">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ba3e3-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="ba3e3-147">Le code utilise également `identity` un élément> <pour spécifier un système de noms de domaine (DNS) de l’identité du serveur attendu.</span><span class="sxs-lookup"><span data-stu-id="ba3e3-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="ba3e3-148">Pour plus d’informations sur l’identité, voir [Identité de service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ba3e3-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba3e3-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba3e3-149">See also</span></span>

- [<span data-ttu-id="ba3e3-150">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="ba3e3-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="ba3e3-151">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ba3e3-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ba3e3-152">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="ba3e3-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="ba3e3-153">[Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ba3e3-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
