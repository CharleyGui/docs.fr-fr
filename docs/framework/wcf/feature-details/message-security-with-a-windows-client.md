---
title: Sécurité de message avec un client Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: c87583bec908c3465dedf7c542e30ce264cd7b47
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553777"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="d46b9-102">Sécurité de message avec un client Windows</span><span class="sxs-lookup"><span data-stu-id="d46b9-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="d46b9-103">Ce scénario montre un client Windows Communication Foundation (WCF) et un serveur sécurisés par le mode de sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="d46b9-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="d46b9-104">Le client et le service sont authentifiés à l'aide des informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="d46b9-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="d46b9-105">![Sécurité des messages avec un client Windows](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="d46b9-105">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="d46b9-106">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="d46b9-106">Characteristic</span></span>|<span data-ttu-id="d46b9-107">Description</span><span class="sxs-lookup"><span data-stu-id="d46b9-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d46b9-108">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="d46b9-108">Security Mode</span></span>|<span data-ttu-id="d46b9-109">Message</span><span class="sxs-lookup"><span data-stu-id="d46b9-109">Message</span></span>|  
|<span data-ttu-id="d46b9-110">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d46b9-110">Interoperability</span></span>|<span data-ttu-id="d46b9-111">WCF uniquement</span><span class="sxs-lookup"><span data-stu-id="d46b9-111">WCF Only</span></span>|  
|<span data-ttu-id="d46b9-112">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="d46b9-112">Authentication (Server)</span></span>|<span data-ttu-id="d46b9-113">Authentification mutuelle du serveur et du client</span><span class="sxs-lookup"><span data-stu-id="d46b9-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="d46b9-114">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="d46b9-114">Authentication (Client)</span></span>|<span data-ttu-id="d46b9-115">Authentification mutuelle du serveur et du client</span><span class="sxs-lookup"><span data-stu-id="d46b9-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="d46b9-116">Intégrité</span><span class="sxs-lookup"><span data-stu-id="d46b9-116">Integrity</span></span>|<span data-ttu-id="d46b9-117">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="d46b9-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d46b9-118">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="d46b9-118">Confidentiality</span></span>|<span data-ttu-id="d46b9-119">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="d46b9-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d46b9-120">Transport</span><span class="sxs-lookup"><span data-stu-id="d46b9-120">Transport</span></span>|<span data-ttu-id="d46b9-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="d46b9-121">NET.TCP</span></span>|  
|<span data-ttu-id="d46b9-122">Liaison</span><span class="sxs-lookup"><span data-stu-id="d46b9-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d46b9-123">Service</span><span class="sxs-lookup"><span data-stu-id="d46b9-123">Service</span></span>  
 <span data-ttu-id="d46b9-124">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="d46b9-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d46b9-125">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d46b9-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="d46b9-126">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="d46b9-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d46b9-127">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d46b9-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d46b9-128">Code</span><span class="sxs-lookup"><span data-stu-id="d46b9-128">Code</span></span>  
 <span data-ttu-id="d46b9-129">Le code suivant indique comment créer un point de terminaison de service qui utilise la sécurité de message pour établir un contexte sécurisé lorsqu'un ordinateur sous Windows est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d46b9-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="d46b9-130">Configuration</span><span class="sxs-lookup"><span data-stu-id="d46b9-130">Configuration</span></span>  
 <span data-ttu-id="d46b9-131">La configuration suivante peut être utilisée à la place du code pour paramétrer le service :</span><span class="sxs-lookup"><span data-stu-id="d46b9-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="d46b9-132">Client</span><span class="sxs-lookup"><span data-stu-id="d46b9-132">Client</span></span>  
 <span data-ttu-id="d46b9-133">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="d46b9-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d46b9-134">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d46b9-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="d46b9-135">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="d46b9-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="d46b9-136">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d46b9-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d46b9-137">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="d46b9-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d46b9-138">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d46b9-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d46b9-139">Code</span><span class="sxs-lookup"><span data-stu-id="d46b9-139">Code</span></span>  
 <span data-ttu-id="d46b9-140">Le code suivant crée un client.</span><span class="sxs-lookup"><span data-stu-id="d46b9-140">The following code creates a client.</span></span> <span data-ttu-id="d46b9-141">La liaison est définie au mode de sécurité de niveau message et le type d’informations d’identification du client a la valeur `Windows`.</span><span class="sxs-lookup"><span data-stu-id="d46b9-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="d46b9-142">Configuration</span><span class="sxs-lookup"><span data-stu-id="d46b9-142">Configuration</span></span>  
 <span data-ttu-id="d46b9-143">La configuration suivante est utilisée pour définir les propriétés du client.</span><span class="sxs-lookup"><span data-stu-id="d46b9-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d46b9-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d46b9-144">See also</span></span>

- [<span data-ttu-id="d46b9-145">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="d46b9-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="d46b9-146">[Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d46b9-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
