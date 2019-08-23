---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 806cf8524ed1a1439ca85a4b918e8e486e5dc94b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936589"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="66452-102">\<> de sécurité \<de WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="66452-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="66452-103">Spécifie les exigences de sécurité pour un point de terminaison configuré avec un [ \<> WebHttpBinding](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="66452-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="66452-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="66452-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="66452-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="66452-105">\<bindings></span></span>  
<span data-ttu-id="66452-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="66452-106">\<webHttpBinding></span></span>  
<span data-ttu-id="66452-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="66452-107">\<binding></span></span>  
<span data-ttu-id="66452-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="66452-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66452-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66452-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66452-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="66452-110">Attributes and Elements</span></span>  
 <span data-ttu-id="66452-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="66452-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66452-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="66452-112">Attributes</span></span>  
  
|<span data-ttu-id="66452-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="66452-113">Attribute</span></span>|<span data-ttu-id="66452-114">Description</span><span class="sxs-lookup"><span data-stu-id="66452-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66452-115">mode</span><span class="sxs-lookup"><span data-stu-id="66452-115">mode</span></span>|<span data-ttu-id="66452-116">Indique si un point de terminaison utilise la sécurité au niveau du transport ou s'il n'utilise aucune sécurité.</span><span class="sxs-lookup"><span data-stu-id="66452-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="66452-117">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="66452-117">The default is `None`.</span></span> <span data-ttu-id="66452-118">Cet attribut est de type <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="66452-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="66452-119">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="66452-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="66452-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="66452-120">Value</span></span>|<span data-ttu-id="66452-121">Description</span><span class="sxs-lookup"><span data-stu-id="66452-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66452-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="66452-122">None</span></span>|<span data-ttu-id="66452-123">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="66452-123">Security is disabled.</span></span>|  
|<span data-ttu-id="66452-124">Transport</span><span class="sxs-lookup"><span data-stu-id="66452-124">Transport</span></span>|<span data-ttu-id="66452-125">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="66452-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="66452-126">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="66452-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="66452-127">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="66452-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="66452-128">L’authentification du client est contrôlée par `ClientCredentialType` le biais [ \<](transport-of-webhttpbinding.md)de l’attribut du > de transport.</span><span class="sxs-lookup"><span data-stu-id="66452-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="66452-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="66452-129">TransportCredentialOnly</span></span>|<span data-ttu-id="66452-130">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="66452-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="66452-131">Il fournit l'authentification du client basée sur le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="66452-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="66452-132">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="66452-132">This mode should be used with caution.</span></span> <span data-ttu-id="66452-133">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="66452-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66452-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="66452-134">Child Elements</span></span>  
  
|<span data-ttu-id="66452-135">Élément</span><span class="sxs-lookup"><span data-stu-id="66452-135">Element</span></span>|<span data-ttu-id="66452-136">Description</span><span class="sxs-lookup"><span data-stu-id="66452-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66452-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="66452-137">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="66452-138">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="66452-138">Defines the transport security settings.</span></span> <span data-ttu-id="66452-139">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="66452-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66452-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="66452-140">Parent Elements</span></span>  
  
|<span data-ttu-id="66452-141">Élément</span><span class="sxs-lookup"><span data-stu-id="66452-141">Element</span></span>|<span data-ttu-id="66452-142">Description</span><span class="sxs-lookup"><span data-stu-id="66452-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66452-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="66452-143">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="66452-144">Élément de liaison utilisé pour configurer des points de terminaison pour les services Web Windows Communication Foundation (WCF) qui répondent aux requêtes HTTP au lieu des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="66452-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66452-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66452-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="66452-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="66452-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="66452-147">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="66452-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="66452-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="66452-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66452-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="66452-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="66452-150">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="66452-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="66452-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="66452-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="66452-152">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="66452-152">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
