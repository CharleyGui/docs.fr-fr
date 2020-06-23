---
title: Sécurité de transport avec un client anonyme
description: Passez en revue ce scénario WCF, qui utilise la sécurité de transport pour authentifier un serveur à l’aide d’un certificat approuvé par le client. Le client n’est pas authentifié.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245009"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="a6b94-104">Sécurité de transport avec un client anonyme</span><span class="sxs-lookup"><span data-stu-id="a6b94-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="a6b94-105">Ce scénario de Windows Communication Foundation (WCF) utilise la sécurité de transport (HTTPs) pour garantir la confidentialité et l’intégrité.</span><span class="sxs-lookup"><span data-stu-id="a6b94-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="a6b94-106">Le serveur doit être authentifié à l'aide d'un certificat SSL (Secure Sockets Layer). Les clients doivent ensuite faire confiance à ce certificat.</span><span class="sxs-lookup"><span data-stu-id="a6b94-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="a6b94-107">Aucun mécanisme n'authentifie les clients, ceux-ci restent donc anonymes.</span><span class="sxs-lookup"><span data-stu-id="a6b94-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="a6b94-108">Pour obtenir un exemple d’application, consultez la page relative à la [sécurité du transport WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="a6b94-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="a6b94-109">Pour plus d’informations sur la sécurité du transport, consultez [vue d’ensemble de la sécurité du transport](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a6b94-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="a6b94-110">Pour plus d’informations sur l’utilisation d’un certificat avec un service, consultez [utilisation des certificats](working-with-certificates.md) et [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a6b94-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Utilisation de la sécurité de transport avec un client anonyme](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="a6b94-112">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="a6b94-112">Characteristic</span></span>|<span data-ttu-id="a6b94-113">Description</span><span class="sxs-lookup"><span data-stu-id="a6b94-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="a6b94-114">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="a6b94-114">Security Mode</span></span>|<span data-ttu-id="a6b94-115">Transport</span><span class="sxs-lookup"><span data-stu-id="a6b94-115">Transport</span></span>|
|<span data-ttu-id="a6b94-116">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="a6b94-116">Interoperability</span></span>|<span data-ttu-id="a6b94-117">Avec les services Web et les clients existants</span><span class="sxs-lookup"><span data-stu-id="a6b94-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="a6b94-118">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="a6b94-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="a6b94-119">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="a6b94-119">Authentication (Client)</span></span>|<span data-ttu-id="a6b94-120">Yes</span><span class="sxs-lookup"><span data-stu-id="a6b94-120">Yes</span></span><br /><br /> <span data-ttu-id="a6b94-121">Niveau de l’application (aucune prise en charge WCF)</span><span class="sxs-lookup"><span data-stu-id="a6b94-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="a6b94-122">Intégrité</span><span class="sxs-lookup"><span data-stu-id="a6b94-122">Integrity</span></span>|<span data-ttu-id="a6b94-123">Yes</span><span class="sxs-lookup"><span data-stu-id="a6b94-123">Yes</span></span>|
|<span data-ttu-id="a6b94-124">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="a6b94-124">Confidentiality</span></span>|<span data-ttu-id="a6b94-125">Yes</span><span class="sxs-lookup"><span data-stu-id="a6b94-125">Yes</span></span>|
|<span data-ttu-id="a6b94-126">Transport</span><span class="sxs-lookup"><span data-stu-id="a6b94-126">Transport</span></span>|<span data-ttu-id="a6b94-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="a6b94-127">HTTPS</span></span>|
|<span data-ttu-id="a6b94-128">Liaison</span><span class="sxs-lookup"><span data-stu-id="a6b94-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="a6b94-129">Service</span><span class="sxs-lookup"><span data-stu-id="a6b94-129">Service</span></span>

<span data-ttu-id="a6b94-130">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="a6b94-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a6b94-131">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6b94-131">Do one of the following:</span></span>

- <span data-ttu-id="a6b94-132">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="a6b94-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="a6b94-133">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a6b94-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="a6b94-134">Code</span><span class="sxs-lookup"><span data-stu-id="a6b94-134">Code</span></span>

<span data-ttu-id="a6b94-135">Le code suivant illustre comment créer un point de terminaison à l'aide de la sécurité de transport :</span><span class="sxs-lookup"><span data-stu-id="a6b94-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="a6b94-136">Configuration</span><span class="sxs-lookup"><span data-stu-id="a6b94-136">Configuration</span></span>

<span data-ttu-id="a6b94-137">Le code ci-dessous configure le même point de terminaison en utilisant la configuration.</span><span class="sxs-lookup"><span data-stu-id="a6b94-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="a6b94-138">Aucun mécanisme n'authentifie les clients, ceux-ci restent donc anonymes.</span><span class="sxs-lookup"><span data-stu-id="a6b94-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="a6b94-139">Client</span><span class="sxs-lookup"><span data-stu-id="a6b94-139">Client</span></span>

<span data-ttu-id="a6b94-140">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="a6b94-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a6b94-141">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6b94-141">Do one of the following:</span></span>

- <span data-ttu-id="a6b94-142">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="a6b94-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="a6b94-143">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a6b94-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a6b94-144">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="a6b94-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a6b94-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a6b94-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="a6b94-146">Code</span><span class="sxs-lookup"><span data-stu-id="a6b94-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="a6b94-147">Configuration</span><span class="sxs-lookup"><span data-stu-id="a6b94-147">Configuration</span></span>

<span data-ttu-id="a6b94-148">La configuration suivante peut être utilisée à la place du code pour paramétrer le service :</span><span class="sxs-lookup"><span data-stu-id="a6b94-148">The following configuration can be used instead of the code to set up the service.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a6b94-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6b94-149">See also</span></span>

- [<span data-ttu-id="a6b94-150">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="a6b94-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="a6b94-151">WS Transport Security</span><span class="sxs-lookup"><span data-stu-id="a6b94-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="a6b94-152">Vue d'ensemble de la sécurité des transports</span><span class="sxs-lookup"><span data-stu-id="a6b94-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="a6b94-153">[Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a6b94-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
