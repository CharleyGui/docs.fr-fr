---
title: Sécurité de transport avec l'authentification de base
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 7c83de70e404fe8304bc2e35c1bb5df9e42f95b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576094"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="f5d53-102">Sécurité de transport avec l'authentification de base</span><span class="sxs-lookup"><span data-stu-id="f5d53-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="f5d53-103">L’illustration suivante montre un service et un client Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f5d53-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="f5d53-104">Le serveur nécessite un certificat X.509 valide qui peut être utilisé pour SSL (Secure Sockets Layer) et les clients doivent approuver le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5d53-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="f5d53-105">De plus, le service Web contient déjà une implémentation SSL disponible.</span><span class="sxs-lookup"><span data-stu-id="f5d53-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="f5d53-106">Pour plus d’informations sur l’activation de l’authentification de base sur les Internet Information Services (IIS), consultez <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .</span><span class="sxs-lookup"><span data-stu-id="f5d53-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Capture d’écran montrant la sécurité de transport avec l’authentification de base.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="f5d53-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="f5d53-108">Characteristic</span></span>|<span data-ttu-id="f5d53-109">Description</span><span class="sxs-lookup"><span data-stu-id="f5d53-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f5d53-110">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="f5d53-110">Security Mode</span></span>|<span data-ttu-id="f5d53-111">Transport</span><span class="sxs-lookup"><span data-stu-id="f5d53-111">Transport</span></span>|  
|<span data-ttu-id="f5d53-112">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f5d53-112">Interoperability</span></span>|<span data-ttu-id="f5d53-113">Avec les clients de service Web et les services existants</span><span class="sxs-lookup"><span data-stu-id="f5d53-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="f5d53-114">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="f5d53-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="f5d53-115">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="f5d53-115">Authentication (Client)</span></span>|<span data-ttu-id="f5d53-116">Oui (à l'aide de HTTPS)</span><span class="sxs-lookup"><span data-stu-id="f5d53-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="f5d53-117">Oui (à l'aide du Nom d'utilisateur/Mot de passe)</span><span class="sxs-lookup"><span data-stu-id="f5d53-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="f5d53-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="f5d53-118">Integrity</span></span>|<span data-ttu-id="f5d53-119">Oui</span><span class="sxs-lookup"><span data-stu-id="f5d53-119">Yes</span></span>|  
|<span data-ttu-id="f5d53-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="f5d53-120">Confidentiality</span></span>|<span data-ttu-id="f5d53-121">Oui</span><span class="sxs-lookup"><span data-stu-id="f5d53-121">Yes</span></span>|  
|<span data-ttu-id="f5d53-122">Transport</span><span class="sxs-lookup"><span data-stu-id="f5d53-122">Transport</span></span>|<span data-ttu-id="f5d53-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="f5d53-123">HTTPS</span></span>|  
|<span data-ttu-id="f5d53-124">Liaison</span><span class="sxs-lookup"><span data-stu-id="f5d53-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f5d53-125">Service</span><span class="sxs-lookup"><span data-stu-id="f5d53-125">Service</span></span>  
 <span data-ttu-id="f5d53-126">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="f5d53-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f5d53-127">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5d53-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="f5d53-128">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="f5d53-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f5d53-129">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f5d53-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5d53-130">Code</span><span class="sxs-lookup"><span data-stu-id="f5d53-130">Code</span></span>  
 <span data-ttu-id="f5d53-131">Le code suivant montre comment créer un point de terminaison de service qui utilise un nom d'utilisateur de domaine et un mot de passe Windows pour la sécurité de transfert.</span><span class="sxs-lookup"><span data-stu-id="f5d53-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="f5d53-132">Notez que le service requiert un certificat X.509 pour s'authentifier auprès du client.</span><span class="sxs-lookup"><span data-stu-id="f5d53-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="f5d53-133">Pour plus d’informations, consultez [utilisation des certificats](working-with-certificates.md) et [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="f5d53-133">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="f5d53-134">Configuration</span><span class="sxs-lookup"><span data-stu-id="f5d53-134">Configuration</span></span>  
 <span data-ttu-id="f5d53-135">Les éléments suivants configurent un service pour utiliser l'authentification de base avec la sécurité au niveau du transport :</span><span class="sxs-lookup"><span data-stu-id="f5d53-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="f5d53-136">Client</span><span class="sxs-lookup"><span data-stu-id="f5d53-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5d53-137">Code</span><span class="sxs-lookup"><span data-stu-id="f5d53-137">Code</span></span>  
 <span data-ttu-id="f5d53-138">Le code suivant affiche le code client qui inclut le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f5d53-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="f5d53-139">Notez que l'utilisateur doit fournir un nom d'utilisateur et un mot de passe Windows valides.</span><span class="sxs-lookup"><span data-stu-id="f5d53-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="f5d53-140">Le code pour retourner le nom d'utilisateur et le mot de passe n'est pas indiqué.</span><span class="sxs-lookup"><span data-stu-id="f5d53-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="f5d53-141">Utilisez une boîte de dialogue ou une autre interface pour demander les informations à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5d53-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5d53-142">Le nom d'utilisateur et le mot de passe peuvent être définis uniquement à l'aide de code.</span><span class="sxs-lookup"><span data-stu-id="f5d53-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="f5d53-143">Configuration</span><span class="sxs-lookup"><span data-stu-id="f5d53-143">Configuration</span></span>  
 <span data-ttu-id="f5d53-144">Le code suivant affiche la configuration du client.</span><span class="sxs-lookup"><span data-stu-id="f5d53-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5d53-145">Vous ne pouvez pas utiliser la configuration pour définir le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f5d53-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="f5d53-146">La configuration indiquée ici doit être augmentée à l'aide du code pour définir le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f5d53-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
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
  
## <a name="see-also"></a><span data-ttu-id="f5d53-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5d53-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="f5d53-148">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="f5d53-148">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="f5d53-149">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="f5d53-149">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="f5d53-150">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="f5d53-150">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="f5d53-151">[Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f5d53-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
