---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397860"
---
# <a name="localissuer"></a><span data-ttu-id="cc161-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="cc161-101">\<localIssuer></span></span>
<span data-ttu-id="cc161-102">Spécifie l'adresse et la liaison de l'émetteur local à utiliser pour obtenir un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="cc161-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="cc161-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc161-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cc161-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cc161-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="cc161-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="cc161-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="cc161-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="cc161-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="cc161-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localIssuer >**</span><span class="sxs-lookup"><span data-stu-id="cc161-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc161-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc161-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc161-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cc161-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cc161-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cc161-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc161-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="cc161-114">Attributes</span></span>  
  
|<span data-ttu-id="cc161-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="cc161-115">Attribute</span></span>|<span data-ttu-id="cc161-116">Description</span><span class="sxs-lookup"><span data-stu-id="cc161-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc161-117">adresse</span><span class="sxs-lookup"><span data-stu-id="cc161-117">address</span></span>|<span data-ttu-id="cc161-118">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="cc161-118">Required string.</span></span> <span data-ttu-id="cc161-119">Spécifie l'URI de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="cc161-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="cc161-120">liaison</span><span class="sxs-lookup"><span data-stu-id="cc161-120">binding</span></span>|<span data-ttu-id="cc161-121">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="cc161-121">Optional string.</span></span> <span data-ttu-id="cc161-122">Une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="cc161-122">One of the system-provided bindings.</span></span> <span data-ttu-id="cc161-123">Pour obtenir une liste, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="cc161-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="cc161-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc161-124">bindingConfiguration</span></span>|<span data-ttu-id="cc161-125">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="cc161-125">Optional string.</span></span> <span data-ttu-id="cc161-126">Spécifie une configuration de liaison recherchée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cc161-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc161-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cc161-127">Child Elements</span></span>  
  
|<span data-ttu-id="cc161-128">Élément</span><span class="sxs-lookup"><span data-stu-id="cc161-128">Element</span></span>|<span data-ttu-id="cc161-129">Description</span><span class="sxs-lookup"><span data-stu-id="cc161-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc161-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="cc161-130">\<identity></span></span>](identity.md)|<span data-ttu-id="cc161-131">Spécifie les informations d'identité de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="cc161-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="cc161-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="cc161-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="cc161-133">Collection d'en-têtes d'adresse requis pour adresser correctement l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="cc161-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="cc161-134">Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.</span><span class="sxs-lookup"><span data-stu-id="cc161-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc161-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cc161-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cc161-136">Élément</span><span class="sxs-lookup"><span data-stu-id="cc161-136">Element</span></span>|<span data-ttu-id="cc161-137">Description</span><span class="sxs-lookup"><span data-stu-id="cc161-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc161-138">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="cc161-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="cc161-139">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="cc161-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc161-140">Notes</span><span class="sxs-lookup"><span data-stu-id="cc161-140">Remarks</span></span>  
 <span data-ttu-id="cc161-141">Lors de l'obtention d'un jeton émis depuis un service d'émission de jeton de sécurité (STS), l'application cliente doit être configurée avec l'adresse et la liaison à utiliser pour pouvoir communiquer avec le STS.</span><span class="sxs-lookup"><span data-stu-id="cc161-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="cc161-142">Lorsque ne fournit pas d’URL pour le service d’émission de jeton de sécurité, ou lorsque l’adresse de l’émetteur d' `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` une `null`liaison fédérée est ou, le canal de Windows Communication Foundation (WCF) du client utilise les valeurs spécifiées par <xref:System.ServiceModel.WSFederationHttpBinding> `address` et`binding` communiquent avec le STS pour obtenir le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="cc161-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="cc161-143">Pour plus d’informations sur la configuration d’un émetteur local, [consultez Procédure : Configurez un émetteur](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="cc161-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc161-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="cc161-144">Example</span></span>  
 <span data-ttu-id="cc161-145">L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.</span><span class="sxs-lookup"><span data-stu-id="cc161-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc161-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc161-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="cc161-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="cc161-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cc161-148">Guide pratique : Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="cc161-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="cc161-149">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="cc161-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cc161-150">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="cc161-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cc161-151">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="cc161-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cc161-152">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="cc161-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cc161-153">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="cc161-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="cc161-154">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="cc161-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="cc161-155">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="cc161-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
