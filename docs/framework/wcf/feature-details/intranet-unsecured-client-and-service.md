---
title: Service et client intranet non sécurisés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 65b8597727da256e832351792b9d5d9bd016eb28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587008"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="0fe83-102">Service et client intranet non sécurisés</span><span class="sxs-lookup"><span data-stu-id="0fe83-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="0fe83-103">L’illustration suivante représente un service Windows Communication Foundation (WCF) simple développé pour fournir des informations sur un réseau privé sécurisé à une application WCF.</span><span class="sxs-lookup"><span data-stu-id="0fe83-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="0fe83-104">Sécurité n’est pas nécessaire, car les données sont d’importance basse, le réseau doit être sécurisé par nature, ou sécurité est fournie par une couche ci-dessous l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="0fe83-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Scénario de service et client intranet non sécurisés.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="0fe83-106">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="0fe83-106">Characteristic</span></span>|<span data-ttu-id="0fe83-107">Description</span><span class="sxs-lookup"><span data-stu-id="0fe83-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0fe83-108">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="0fe83-108">Security Mode</span></span>|<span data-ttu-id="0fe83-109">None</span><span class="sxs-lookup"><span data-stu-id="0fe83-109">None</span></span>|  
|<span data-ttu-id="0fe83-110">Transport</span><span class="sxs-lookup"><span data-stu-id="0fe83-110">Transport</span></span>|<span data-ttu-id="0fe83-111">TCP</span><span class="sxs-lookup"><span data-stu-id="0fe83-111">TCP</span></span>|  
|<span data-ttu-id="0fe83-112">Liaison</span><span class="sxs-lookup"><span data-stu-id="0fe83-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="0fe83-113">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="0fe83-113">Interoperability</span></span>|<span data-ttu-id="0fe83-114">WCF uniquement</span><span class="sxs-lookup"><span data-stu-id="0fe83-114">WCF only</span></span>|  
|<span data-ttu-id="0fe83-115">Authentification</span><span class="sxs-lookup"><span data-stu-id="0fe83-115">Authentication</span></span>|<span data-ttu-id="0fe83-116">None</span><span class="sxs-lookup"><span data-stu-id="0fe83-116">None</span></span>|  
|<span data-ttu-id="0fe83-117">Intégrité</span><span class="sxs-lookup"><span data-stu-id="0fe83-117">Integrity</span></span>|<span data-ttu-id="0fe83-118">None</span><span class="sxs-lookup"><span data-stu-id="0fe83-118">None</span></span>|  
|<span data-ttu-id="0fe83-119">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="0fe83-119">Confidentiality</span></span>|<span data-ttu-id="0fe83-120">None</span><span class="sxs-lookup"><span data-stu-id="0fe83-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="0fe83-121">Service</span><span class="sxs-lookup"><span data-stu-id="0fe83-121">Service</span></span>  
 <span data-ttu-id="0fe83-122">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="0fe83-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="0fe83-123">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fe83-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="0fe83-124">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="0fe83-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="0fe83-125">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0fe83-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0fe83-126">Code</span><span class="sxs-lookup"><span data-stu-id="0fe83-126">Code</span></span>  
 <span data-ttu-id="0fe83-127">Le code ci-dessous montre comment créer un point de terminaison sans sécurité :</span><span class="sxs-lookup"><span data-stu-id="0fe83-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="0fe83-128">Configuration</span><span class="sxs-lookup"><span data-stu-id="0fe83-128">Configuration</span></span>  
 <span data-ttu-id="0fe83-129">Le code ci-dessous configure le même point de terminaison en utilisant la configuration :</span><span class="sxs-lookup"><span data-stu-id="0fe83-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="0fe83-130">Client</span><span class="sxs-lookup"><span data-stu-id="0fe83-130">Client</span></span>  
 <span data-ttu-id="0fe83-131">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="0fe83-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="0fe83-132">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fe83-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="0fe83-133">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="0fe83-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="0fe83-134">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0fe83-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="0fe83-135">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="0fe83-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="0fe83-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0fe83-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="0fe83-137">Code</span><span class="sxs-lookup"><span data-stu-id="0fe83-137">Code</span></span>  
 <span data-ttu-id="0fe83-138">Le code suivant montre un client WCF de base qui accède à un point de terminaison non sécurisé à l’aide du protocole TCP.</span><span class="sxs-lookup"><span data-stu-id="0fe83-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="0fe83-139">Configuration</span><span class="sxs-lookup"><span data-stu-id="0fe83-139">Configuration</span></span>  
 <span data-ttu-id="0fe83-140">Le code de configuration suivant s'applique au client :</span><span class="sxs-lookup"><span data-stu-id="0fe83-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe83-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fe83-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="0fe83-142">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="0fe83-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="0fe83-143">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="0fe83-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
