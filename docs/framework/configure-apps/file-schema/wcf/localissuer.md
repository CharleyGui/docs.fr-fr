---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931743"
---
# <a name="localissuer"></a><span data-ttu-id="2f686-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="2f686-101">\<localIssuer></span></span>
<span data-ttu-id="2f686-102">Spécifie l'adresse et la liaison de l'émetteur local à utiliser pour obtenir un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2f686-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="2f686-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2f686-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2f686-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2f686-104">\<behaviors></span></span>  
<span data-ttu-id="2f686-105">section endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2f686-105">endpointBehaviors section</span></span>  
<span data-ttu-id="2f686-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="2f686-106">\<behavior></span></span>  
<span data-ttu-id="2f686-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2f686-107">\<clientCredentials></span></span>  
<span data-ttu-id="2f686-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="2f686-108">\<issuedToken></span></span>  
<span data-ttu-id="2f686-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="2f686-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f686-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f686-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f686-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f686-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2f686-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f686-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f686-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f686-113">Attributes</span></span>  
  
|<span data-ttu-id="2f686-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f686-114">Attribute</span></span>|<span data-ttu-id="2f686-115">Description</span><span class="sxs-lookup"><span data-stu-id="2f686-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f686-116">adresse</span><span class="sxs-lookup"><span data-stu-id="2f686-116">address</span></span>|<span data-ttu-id="2f686-117">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="2f686-117">Required string.</span></span> <span data-ttu-id="2f686-118">Spécifie l'URI de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="2f686-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="2f686-119">liaison</span><span class="sxs-lookup"><span data-stu-id="2f686-119">binding</span></span>|<span data-ttu-id="2f686-120">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="2f686-120">Optional string.</span></span> <span data-ttu-id="2f686-121">Une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="2f686-121">One of the system-provided bindings.</span></span> <span data-ttu-id="2f686-122">Pour obtenir une liste, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="2f686-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="2f686-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f686-123">bindingConfiguration</span></span>|<span data-ttu-id="2f686-124">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="2f686-124">Optional string.</span></span> <span data-ttu-id="2f686-125">Spécifie une configuration de liaison recherchée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2f686-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f686-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f686-126">Child Elements</span></span>  
  
|<span data-ttu-id="2f686-127">Élément</span><span class="sxs-lookup"><span data-stu-id="2f686-127">Element</span></span>|<span data-ttu-id="2f686-128">Description</span><span class="sxs-lookup"><span data-stu-id="2f686-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f686-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="2f686-129">\<identity></span></span>](identity.md)|<span data-ttu-id="2f686-130">Spécifie les informations d'identité de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="2f686-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="2f686-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="2f686-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="2f686-132">Collection d'en-têtes d'adresse requis pour adresser correctement l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="2f686-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="2f686-133">Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.</span><span class="sxs-lookup"><span data-stu-id="2f686-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f686-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f686-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2f686-135">Élément</span><span class="sxs-lookup"><span data-stu-id="2f686-135">Element</span></span>|<span data-ttu-id="2f686-136">Description</span><span class="sxs-lookup"><span data-stu-id="2f686-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f686-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="2f686-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="2f686-138">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="2f686-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f686-139">Notes</span><span class="sxs-lookup"><span data-stu-id="2f686-139">Remarks</span></span>  
 <span data-ttu-id="2f686-140">Lors de l'obtention d'un jeton émis depuis un service d'émission de jeton de sécurité (STS), l'application cliente doit être configurée avec l'adresse et la liaison à utiliser pour pouvoir communiquer avec le STS.</span><span class="sxs-lookup"><span data-stu-id="2f686-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="2f686-141">Lorsque ne fournit pas d’URL pour le service d’émission de jeton de sécurité, ou lorsque l’adresse de l’émetteur d' `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` une `null`liaison fédérée est ou, le canal de Windows Communication Foundation (WCF) du client utilise les valeurs spécifiées par <xref:System.ServiceModel.WSFederationHttpBinding> `address` et`binding` communiquent avec le STS pour obtenir le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="2f686-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="2f686-142">Pour plus d’informations sur la configuration d’un émetteur local, [consultez Procédure: Configurez un émetteur](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="2f686-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f686-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f686-143">Example</span></span>  
 <span data-ttu-id="2f686-144">L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.</span><span class="sxs-lookup"><span data-stu-id="2f686-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="2f686-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f686-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="2f686-146">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="2f686-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2f686-147">Guide pratique pour Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="2f686-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2f686-148">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="2f686-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2f686-149">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="2f686-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2f686-150">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2f686-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2f686-151">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="2f686-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f686-152">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="2f686-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2f686-153">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="2f686-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2f686-154">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2f686-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
