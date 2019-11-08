---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738634"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="a47ca-102">\<> de sécurité de \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a47ca-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="a47ca-103">Spécifie les exigences de sécurité pour un point de terminaison configuré avec un [\<webHttpBinding >](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a47ca-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="a47ca-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a47ca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a47ca-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a47ca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a47ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="a47ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="a47ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a47ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="a47ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="a47ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="a47ca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="a47ca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47ca-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a47ca-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a47ca-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a47ca-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a47ca-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a47ca-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a47ca-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a47ca-113">Attributes</span></span>  
  
|<span data-ttu-id="a47ca-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a47ca-114">Attribute</span></span>|<span data-ttu-id="a47ca-115">Description</span><span class="sxs-lookup"><span data-stu-id="a47ca-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a47ca-116">mode</span><span class="sxs-lookup"><span data-stu-id="a47ca-116">mode</span></span>|<span data-ttu-id="a47ca-117">Indique si un point de terminaison utilise la sécurité au niveau du transport ou s'il n'utilise aucune sécurité.</span><span class="sxs-lookup"><span data-stu-id="a47ca-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="a47ca-118">La valeur par défaut est `None`,</span><span class="sxs-lookup"><span data-stu-id="a47ca-118">The default is `None`.</span></span> <span data-ttu-id="a47ca-119">Cet attribut est de type <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a47ca-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a47ca-120">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="a47ca-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="a47ca-121">valeur</span><span class="sxs-lookup"><span data-stu-id="a47ca-121">Value</span></span>|<span data-ttu-id="a47ca-122">Description</span><span class="sxs-lookup"><span data-stu-id="a47ca-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a47ca-123">aucune.</span><span class="sxs-lookup"><span data-stu-id="a47ca-123">None</span></span>|<span data-ttu-id="a47ca-124">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a47ca-124">Security is disabled.</span></span>|  
|<span data-ttu-id="a47ca-125">Transport</span><span class="sxs-lookup"><span data-stu-id="a47ca-125">Transport</span></span>|<span data-ttu-id="a47ca-126">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a47ca-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="a47ca-127">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="a47ca-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="a47ca-128">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="a47ca-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a47ca-129">L’authentification du client est contrôlée via l’attribut `ClientCredentialType` de l' [> de transport\<](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a47ca-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="a47ca-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="a47ca-130">TransportCredentialOnly</span></span>|<span data-ttu-id="a47ca-131">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="a47ca-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="a47ca-132">Il fournit l'authentification du client basée sur le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="a47ca-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="a47ca-133">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="a47ca-133">This mode should be used with caution.</span></span> <span data-ttu-id="a47ca-134">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="a47ca-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a47ca-135">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a47ca-135">Child Elements</span></span>  
  
|<span data-ttu-id="a47ca-136">Élément</span><span class="sxs-lookup"><span data-stu-id="a47ca-136">Element</span></span>|<span data-ttu-id="a47ca-137">Description</span><span class="sxs-lookup"><span data-stu-id="a47ca-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a47ca-138">> de transport \<</span><span class="sxs-lookup"><span data-stu-id="a47ca-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="a47ca-139">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="a47ca-139">Defines the transport security settings.</span></span> <span data-ttu-id="a47ca-140">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a47ca-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a47ca-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a47ca-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a47ca-142">Élément</span><span class="sxs-lookup"><span data-stu-id="a47ca-142">Element</span></span>|<span data-ttu-id="a47ca-143">Description</span><span class="sxs-lookup"><span data-stu-id="a47ca-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a47ca-144">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a47ca-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="a47ca-145">Élément de liaison utilisé pour configurer des points de terminaison pour les services Web Windows Communication Foundation (WCF) qui répondent aux requêtes HTTP au lieu des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="a47ca-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a47ca-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a47ca-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="a47ca-147">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a47ca-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a47ca-148">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="a47ca-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a47ca-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a47ca-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a47ca-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a47ca-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a47ca-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a47ca-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a47ca-152">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="a47ca-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="a47ca-153">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="a47ca-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
