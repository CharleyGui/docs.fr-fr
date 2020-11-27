---
title: Sécurité de message avec un client de type Nom d'utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 7168b393bde626c8c413cda3c7422e0eee4ce267
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292868"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="8216f-102">Sécurité de message avec un client de type Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8216f-102">Message Security with a User Name Client</span></span>

<span data-ttu-id="8216f-103">L’illustration suivante montre un service Windows Communication Foundation (WCF) et un client sécurisé à l’aide de la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="8216f-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="8216f-104">Le service est authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="8216f-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="8216f-105">Le client s'authentifie à l'aide d'un nom d'utilisateur et d'un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8216f-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="8216f-106">Pour obtenir un exemple d’application, consultez [nom d’utilisateur de sécurité du message](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="8216f-106">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="8216f-107">![Sécurité de message utilisant l'authentification par nom d'utilisateur](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="8216f-107">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="8216f-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="8216f-108">Characteristic</span></span>|<span data-ttu-id="8216f-109">Description</span><span class="sxs-lookup"><span data-stu-id="8216f-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8216f-110">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="8216f-110">Security Mode</span></span>|<span data-ttu-id="8216f-111">Message</span><span class="sxs-lookup"><span data-stu-id="8216f-111">Message</span></span>|  
|<span data-ttu-id="8216f-112">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="8216f-112">Interoperability</span></span>|<span data-ttu-id="8216f-113">Windows Communication Foundation (WCF) uniquement</span><span class="sxs-lookup"><span data-stu-id="8216f-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="8216f-114">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="8216f-114">Authentication (Server)</span></span>|<span data-ttu-id="8216f-115">La négociation initiale requiert l'authentification du serveur</span><span class="sxs-lookup"><span data-stu-id="8216f-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="8216f-116">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="8216f-116">Authentication (Client)</span></span>|<span data-ttu-id="8216f-117">Nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="8216f-117">User name/password</span></span>|  
|<span data-ttu-id="8216f-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="8216f-118">Integrity</span></span>|<span data-ttu-id="8216f-119">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="8216f-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="8216f-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="8216f-120">Confidentiality</span></span>|<span data-ttu-id="8216f-121">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="8216f-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="8216f-122">Transport</span><span class="sxs-lookup"><span data-stu-id="8216f-122">Transport</span></span>|<span data-ttu-id="8216f-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="8216f-123">HTTP</span></span>|  
|<span data-ttu-id="8216f-124">Liaison</span><span class="sxs-lookup"><span data-stu-id="8216f-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8216f-125">Service</span><span class="sxs-lookup"><span data-stu-id="8216f-125">Service</span></span>  

 <span data-ttu-id="8216f-126">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="8216f-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8216f-127">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8216f-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="8216f-128">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="8216f-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8216f-129">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8216f-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8216f-130">Code</span><span class="sxs-lookup"><span data-stu-id="8216f-130">Code</span></span>  

 <span data-ttu-id="8216f-131">Le code suivant montre comment créer un point de terminaison de service qui utilise la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="8216f-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="8216f-132">Configuration</span><span class="sxs-lookup"><span data-stu-id="8216f-132">Configuration</span></span>  

 <span data-ttu-id="8216f-133">La configuration suivante peut être utilisée à la place du code :</span><span class="sxs-lookup"><span data-stu-id="8216f-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
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
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="8216f-134">Client</span><span class="sxs-lookup"><span data-stu-id="8216f-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="8216f-135">Code</span><span class="sxs-lookup"><span data-stu-id="8216f-135">Code</span></span>  

 <span data-ttu-id="8216f-136">Le code ci-dessous crée le client.</span><span class="sxs-lookup"><span data-stu-id="8216f-136">The following code creates the client.</span></span> <span data-ttu-id="8216f-137">La liaison s’effectue avec la sécurité en mode de message et le type d’informations d’identification client a la valeur `UserName`.</span><span class="sxs-lookup"><span data-stu-id="8216f-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="8216f-138">Le nom d'utilisateur et le mot de passe peuvent uniquement être spécifiés à l'aide du code (cela n'est pas configurable).</span><span class="sxs-lookup"><span data-stu-id="8216f-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="8216f-139">Le code permettant de retourner le nom d'utilisateur et le mot de passe n'est pas indiqué dans ce cas car il doit être exécuté au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="8216f-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="8216f-140">Par exemple, utilisez une boîte de dialogue Windows Forms pour demander les données à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8216f-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="8216f-141">Configuration</span><span class="sxs-lookup"><span data-stu-id="8216f-141">Configuration</span></span>  

 <span data-ttu-id="8216f-142">Le code ci-dessous configure le client.</span><span class="sxs-lookup"><span data-stu-id="8216f-142">The following code configures the client.</span></span> <span data-ttu-id="8216f-143">La liaison s’effectue avec la sécurité en mode de message et le type d’informations d’identification client a la valeur `UserName`.</span><span class="sxs-lookup"><span data-stu-id="8216f-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="8216f-144">Le nom d'utilisateur et le mot de passe peuvent uniquement être spécifiés à l'aide du code (cela n'est pas configurable).</span><span class="sxs-lookup"><span data-stu-id="8216f-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8216f-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8216f-145">See also</span></span>

- [<span data-ttu-id="8216f-146">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="8216f-146">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="8216f-147">Message Security User Name</span><span class="sxs-lookup"><span data-stu-id="8216f-147">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="8216f-148">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="8216f-148">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="8216f-149">[Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8216f-149">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
