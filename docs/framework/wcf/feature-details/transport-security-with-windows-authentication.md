---
title: Sécurité de transport avec l'authentification Windows
description: Passez en revue ce scénario, qui montre un client/service WCF sécurisé par la sécurité Windows. Dans cet exemple, un service intranet affiche des informations sur les ressources humaines.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 9b81f2f2fb6352af254146951ed35ad4fdca8caa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545205"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="cd37d-104">Sécurité de transport avec l'authentification Windows</span><span class="sxs-lookup"><span data-stu-id="cd37d-104">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="cd37d-105">Le scénario suivant montre un client et un service Windows Communication Foundation (WCF) sécurisés par la sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="cd37d-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="cd37d-106">Pour plus d’informations sur la programmation, consultez [Comment : sécuriser un service avec des informations d’identification Windows](../how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="cd37d-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="cd37d-107">Un service Web d'intranet affiche des informations de ressources humaines.</span><span class="sxs-lookup"><span data-stu-id="cd37d-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="cd37d-108">Le client est une application Windows Form.</span><span class="sxs-lookup"><span data-stu-id="cd37d-108">The client is a Windows Form application.</span></span> <span data-ttu-id="cd37d-109">L'application est déployée dans un domaine sécurisé par un contrôleur Kerberos.</span><span class="sxs-lookup"><span data-stu-id="cd37d-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Sécurité de transport avec authentification Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="cd37d-111">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="cd37d-111">Characteristic</span></span>|<span data-ttu-id="cd37d-112">Description</span><span class="sxs-lookup"><span data-stu-id="cd37d-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cd37d-113">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="cd37d-113">Security Mode</span></span>|<span data-ttu-id="cd37d-114">Transport</span><span class="sxs-lookup"><span data-stu-id="cd37d-114">Transport</span></span>|  
|<span data-ttu-id="cd37d-115">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="cd37d-115">Interoperability</span></span>|<span data-ttu-id="cd37d-116">WCF uniquement</span><span class="sxs-lookup"><span data-stu-id="cd37d-116">WCF only</span></span>|  
|<span data-ttu-id="cd37d-117">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="cd37d-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="cd37d-118">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="cd37d-118">Authentication (Client)</span></span>|<span data-ttu-id="cd37d-119">Oui (à l'aide de l'authentification intégrée Windows)</span><span class="sxs-lookup"><span data-stu-id="cd37d-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="cd37d-120">Oui (à l'aide de l'authentification intégrée Windows)</span><span class="sxs-lookup"><span data-stu-id="cd37d-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="cd37d-121">Intégrité</span><span class="sxs-lookup"><span data-stu-id="cd37d-121">Integrity</span></span>|<span data-ttu-id="cd37d-122">Oui</span><span class="sxs-lookup"><span data-stu-id="cd37d-122">Yes</span></span>|  
|<span data-ttu-id="cd37d-123">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="cd37d-123">Confidentiality</span></span>|<span data-ttu-id="cd37d-124">Oui</span><span class="sxs-lookup"><span data-stu-id="cd37d-124">Yes</span></span>|  
|<span data-ttu-id="cd37d-125">Transport</span><span class="sxs-lookup"><span data-stu-id="cd37d-125">Transport</span></span>|<span data-ttu-id="cd37d-126">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="cd37d-126">NET.TCP</span></span>|  
|<span data-ttu-id="cd37d-127">Liaison</span><span class="sxs-lookup"><span data-stu-id="cd37d-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="cd37d-128">Service</span><span class="sxs-lookup"><span data-stu-id="cd37d-128">Service</span></span>  
 <span data-ttu-id="cd37d-129">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="cd37d-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cd37d-130">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="cd37d-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="cd37d-131">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="cd37d-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="cd37d-132">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cd37d-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cd37d-133">Code</span><span class="sxs-lookup"><span data-stu-id="cd37d-133">Code</span></span>  
 <span data-ttu-id="cd37d-134">Le code ci-dessous montre comment créer un point de terminaison de service qui utilise une sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="cd37d-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="cd37d-135">Configuration</span><span class="sxs-lookup"><span data-stu-id="cd37d-135">Configuration</span></span>  
 <span data-ttu-id="cd37d-136">La configuration ci-dessous peut être utilisée à la place du code pour paramétrer le point de terminaison de service :</span><span class="sxs-lookup"><span data-stu-id="cd37d-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="cd37d-137">Client</span><span class="sxs-lookup"><span data-stu-id="cd37d-137">Client</span></span>  
 <span data-ttu-id="cd37d-138">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="cd37d-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cd37d-139">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="cd37d-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="cd37d-140">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="cd37d-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="cd37d-141">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cd37d-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="cd37d-142">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="cd37d-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="cd37d-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="cd37d-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="cd37d-144">Code</span><span class="sxs-lookup"><span data-stu-id="cd37d-144">Code</span></span>  
 <span data-ttu-id="cd37d-145">Le code ci-dessous crée le client.</span><span class="sxs-lookup"><span data-stu-id="cd37d-145">The following code creates the client.</span></span> <span data-ttu-id="cd37d-146">La liaison est configurée de manière à utiliser la sécurité du mode de transport, avec le transport TCP et avec le type Windows d’informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="cd37d-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="cd37d-147">Configuration</span><span class="sxs-lookup"><span data-stu-id="cd37d-147">Configuration</span></span>  
 <span data-ttu-id="cd37d-148">La configuration ci-dessous peut être utilisée à la place du code pour créer le client.</span><span class="sxs-lookup"><span data-stu-id="cd37d-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd37d-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd37d-149">See also</span></span>

- [<span data-ttu-id="cd37d-150">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="cd37d-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="cd37d-151">Procédure : sécuriser un service avec des informations d’identification Windows</span><span class="sxs-lookup"><span data-stu-id="cd37d-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="cd37d-152">[Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cd37d-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
