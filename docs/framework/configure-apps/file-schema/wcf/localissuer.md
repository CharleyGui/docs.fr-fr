---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397860"
---
# \<localIssuer>
<span data-ttu-id="21ae2-101">Spécifie l'adresse et la liaison de l'émetteur local à utiliser pour obtenir un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="21ae2-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="21ae2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21ae2-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21ae2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="21ae2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="21ae2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="21ae2-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21ae2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="21ae2-105">Attributes</span></span>  
  
|<span data-ttu-id="21ae2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="21ae2-106">Attribute</span></span>|<span data-ttu-id="21ae2-107">Description</span><span class="sxs-lookup"><span data-stu-id="21ae2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21ae2-108">address</span><span class="sxs-lookup"><span data-stu-id="21ae2-108">address</span></span>|<span data-ttu-id="21ae2-109">Chaîne obligatoire.</span><span class="sxs-lookup"><span data-stu-id="21ae2-109">Required string.</span></span> <span data-ttu-id="21ae2-110">Spécifie l'URI de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="21ae2-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="21ae2-111">binding</span><span class="sxs-lookup"><span data-stu-id="21ae2-111">binding</span></span>|<span data-ttu-id="21ae2-112">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="21ae2-112">Optional string.</span></span> <span data-ttu-id="21ae2-113">Une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="21ae2-113">One of the system-provided bindings.</span></span> <span data-ttu-id="21ae2-114">Pour obtenir une liste, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="21ae2-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="21ae2-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="21ae2-115">bindingConfiguration</span></span>|<span data-ttu-id="21ae2-116">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="21ae2-116">Optional string.</span></span> <span data-ttu-id="21ae2-117">Spécifie une configuration de liaison recherchée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="21ae2-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21ae2-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21ae2-118">Child Elements</span></span>  
  
|<span data-ttu-id="21ae2-119">Élément</span><span class="sxs-lookup"><span data-stu-id="21ae2-119">Element</span></span>|<span data-ttu-id="21ae2-120">Description</span><span class="sxs-lookup"><span data-stu-id="21ae2-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="21ae2-121">Spécifie les informations d'identité de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="21ae2-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="21ae2-122">Collection d'en-têtes d'adresse requis pour adresser correctement l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="21ae2-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="21ae2-123">Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.</span><span class="sxs-lookup"><span data-stu-id="21ae2-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21ae2-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21ae2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="21ae2-125">Élément</span><span class="sxs-lookup"><span data-stu-id="21ae2-125">Element</span></span>|<span data-ttu-id="21ae2-126">Description</span><span class="sxs-lookup"><span data-stu-id="21ae2-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="21ae2-127">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="21ae2-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21ae2-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="21ae2-128">Remarks</span></span>  
 <span data-ttu-id="21ae2-129">Lors de l'obtention d'un jeton émis depuis un service d'émission de jeton de sécurité (STS), l'application cliente doit être configurée avec l'adresse et la liaison à utiliser pour pouvoir communiquer avec le STS.</span><span class="sxs-lookup"><span data-stu-id="21ae2-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="21ae2-130">Lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d’URL pour le service d’émission de jeton de sécurité, ou lorsque l’adresse de l’émetteur d’une liaison fédérée est `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null` , le canal du Windows Communication Foundation du client (WCF) utilise les valeurs spécifiées par `address` et `binding` pour communiquer avec le STS pour obtenir le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="21ae2-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="21ae2-131">Pour plus d’informations sur la configuration d’un émetteur local, consultez [procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="21ae2-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21ae2-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="21ae2-132">Example</span></span>  
 <span data-ttu-id="21ae2-133">L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.</span><span class="sxs-lookup"><span data-stu-id="21ae2-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21ae2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21ae2-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="21ae2-135">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="21ae2-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="21ae2-136">Comment : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="21ae2-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="21ae2-137">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="21ae2-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="21ae2-138">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="21ae2-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="21ae2-139">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="21ae2-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="21ae2-140">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="21ae2-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="21ae2-141">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="21ae2-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="21ae2-142">Comment : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="21ae2-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="21ae2-143">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="21ae2-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
