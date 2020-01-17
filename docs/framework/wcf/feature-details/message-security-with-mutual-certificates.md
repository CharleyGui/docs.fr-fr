---
title: Sécurité de message avec certificats mutuels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: e784e254fb9314e69457d81a70400f7be30d9c13
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211997"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="89e4b-102">Sécurité de message avec certificats mutuels</span><span class="sxs-lookup"><span data-stu-id="89e4b-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="89e4b-103">Le scénario suivant montre un service Windows Communication Foundation (WCF) et un client sécurisé à l’aide du mode de sécurité message.</span><span class="sxs-lookup"><span data-stu-id="89e4b-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="89e4b-104">Le client et le service sont authentifiés à l'aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="89e4b-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="89e4b-105">Ce scénario est interopérable car il utilise WS-Security avec le profil de jeton de certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="89e4b-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89e4b-106">Ce scénario n'effectue pas la négociation du certificat de service.</span><span class="sxs-lookup"><span data-stu-id="89e4b-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="89e4b-107">Le certificat de service doit être fourni au client avant toute communication.</span><span class="sxs-lookup"><span data-stu-id="89e4b-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="89e4b-108">Le certificat de serveur peut être distribué avec l'application ou fourni dans une communication hors plage.</span><span class="sxs-lookup"><span data-stu-id="89e4b-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="89e4b-109">![Sécurité de message avec certificats mutuels](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="89e4b-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="89e4b-110">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="89e4b-110">Characteristic</span></span>|<span data-ttu-id="89e4b-111">Description</span><span class="sxs-lookup"><span data-stu-id="89e4b-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="89e4b-112">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="89e4b-112">Security Mode</span></span>|<span data-ttu-id="89e4b-113">Message</span><span class="sxs-lookup"><span data-stu-id="89e4b-113">Message</span></span>|  
|<span data-ttu-id="89e4b-114">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="89e4b-114">Interoperability</span></span>|<span data-ttu-id="89e4b-115">Oui, avec WS-Security et des clients et des services compatibles avec le profil de jeton de certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="89e4b-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="89e4b-116">Authentification</span><span class="sxs-lookup"><span data-stu-id="89e4b-116">Authentication</span></span>|<span data-ttu-id="89e4b-117">Authentification mutuelle du serveur et du client.</span><span class="sxs-lookup"><span data-stu-id="89e4b-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="89e4b-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="89e4b-118">Integrity</span></span>|<span data-ttu-id="89e4b-119">Oui</span><span class="sxs-lookup"><span data-stu-id="89e4b-119">Yes</span></span>|  
|<span data-ttu-id="89e4b-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="89e4b-120">Confidentiality</span></span>|<span data-ttu-id="89e4b-121">Oui</span><span class="sxs-lookup"><span data-stu-id="89e4b-121">Yes</span></span>|  
|<span data-ttu-id="89e4b-122">Transport</span><span class="sxs-lookup"><span data-stu-id="89e4b-122">Transport</span></span>|<span data-ttu-id="89e4b-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="89e4b-123">HTTP</span></span>|  
|<span data-ttu-id="89e4b-124">Liaison</span><span class="sxs-lookup"><span data-stu-id="89e4b-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="89e4b-125">Service</span><span class="sxs-lookup"><span data-stu-id="89e4b-125">Service</span></span>  
 <span data-ttu-id="89e4b-126">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="89e4b-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="89e4b-127">Effectuez l'une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="89e4b-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="89e4b-128">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="89e4b-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="89e4b-129">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="89e4b-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89e4b-130">Code</span><span class="sxs-lookup"><span data-stu-id="89e4b-130">Code</span></span>  
 <span data-ttu-id="89e4b-131">Le code ci-dessous crée un point de terminaison de service qui utilise la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="89e4b-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="89e4b-132">Le service requiert un certificat pour s'authentifier.</span><span class="sxs-lookup"><span data-stu-id="89e4b-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="89e4b-133">Configuration</span><span class="sxs-lookup"><span data-stu-id="89e4b-133">Configuration</span></span>  
 <span data-ttu-id="89e4b-134">La configuration ci-dessous peut être utilisée à la place du code pour créer le même service.</span><span class="sxs-lookup"><span data-stu-id="89e4b-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"   
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="89e4b-135">Client</span><span class="sxs-lookup"><span data-stu-id="89e4b-135">Client</span></span>  
 <span data-ttu-id="89e4b-136">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="89e4b-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="89e4b-137">Effectuez l'une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="89e4b-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="89e4b-138">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="89e4b-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="89e4b-139">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="89e4b-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="89e4b-140">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="89e4b-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="89e4b-141">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="89e4b-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="89e4b-142">Code</span><span class="sxs-lookup"><span data-stu-id="89e4b-142">Code</span></span>  
 <span data-ttu-id="89e4b-143">Le code ci-dessous crée le client.</span><span class="sxs-lookup"><span data-stu-id="89e4b-143">The following code creates the client.</span></span> <span data-ttu-id="89e4b-144">Le mode de sécurité a la valeur Message et le type d'informations d'identification client a la valeur Certificat.</span><span class="sxs-lookup"><span data-stu-id="89e4b-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="89e4b-145">Configuration</span><span class="sxs-lookup"><span data-stu-id="89e4b-145">Configuration</span></span>  
 <span data-ttu-id="89e4b-146">Les éléments ci-dessous configurent le client.</span><span class="sxs-lookup"><span data-stu-id="89e4b-146">The following configures the client.</span></span> <span data-ttu-id="89e4b-147">Un certificat client doit être spécifié à l’aide de la [\<ClientCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="89e4b-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="89e4b-148">En outre, le certificat de service est spécifié à l’aide de la [\<DefaultCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="89e4b-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89e4b-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e4b-149">See also</span></span>

- [<span data-ttu-id="89e4b-150">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="89e4b-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="89e4b-151">[Modèle de sécurité pour Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="89e4b-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="89e4b-152">[Comment : créer et installer des certificats temporaires dans WCF pour la sécurité du transport pendant le développement](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="89e4b-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
