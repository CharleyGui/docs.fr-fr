---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 60b863a0a2a846a60dde2e4b323a305b5096b1cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169893"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="a549c-102">\<security> de \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a549c-102">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="a549c-103">Spécifie les exigences de sécurité pour un point de terminaison configuré avec un [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a549c-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a549c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a549c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a549c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a549c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a549c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a549c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a549c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a549c-107">Attributes</span></span>  
  
|<span data-ttu-id="a549c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a549c-108">Attribute</span></span>|<span data-ttu-id="a549c-109">Description</span><span class="sxs-lookup"><span data-stu-id="a549c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a549c-110">mode</span><span class="sxs-lookup"><span data-stu-id="a549c-110">mode</span></span>|<span data-ttu-id="a549c-111">Indique si un point de terminaison utilise la sécurité au niveau du transport ou s'il n'utilise aucune sécurité.</span><span class="sxs-lookup"><span data-stu-id="a549c-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="a549c-112">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="a549c-112">The default is `None`.</span></span> <span data-ttu-id="a549c-113">Cet attribut est de type <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a549c-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a549c-114">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="a549c-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="a549c-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="a549c-115">Value</span></span>|<span data-ttu-id="a549c-116">Description</span><span class="sxs-lookup"><span data-stu-id="a549c-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a549c-117">None</span><span class="sxs-lookup"><span data-stu-id="a549c-117">None</span></span>|<span data-ttu-id="a549c-118">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a549c-118">Security is disabled.</span></span>|  
|<span data-ttu-id="a549c-119">Transport</span><span class="sxs-lookup"><span data-stu-id="a549c-119">Transport</span></span>|<span data-ttu-id="a549c-120">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a549c-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="a549c-121">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="a549c-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="a549c-122">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="a549c-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a549c-123">L’authentification du client est contrôlée par le biais `ClientCredentialType` de l’attribut de [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a549c-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="a549c-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="a549c-124">TransportCredentialOnly</span></span>|<span data-ttu-id="a549c-125">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="a549c-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="a549c-126">Il fournit l'authentification du client basée sur le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="a549c-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="a549c-127">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="a549c-127">This mode should be used with caution.</span></span> <span data-ttu-id="a549c-128">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="a549c-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a549c-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a549c-129">Child Elements</span></span>  
  
|<span data-ttu-id="a549c-130">Élément</span><span class="sxs-lookup"><span data-stu-id="a549c-130">Element</span></span>|<span data-ttu-id="a549c-131">Description</span><span class="sxs-lookup"><span data-stu-id="a549c-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="a549c-132">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="a549c-132">Defines the transport security settings.</span></span> <span data-ttu-id="a549c-133">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a549c-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a549c-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a549c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a549c-135">Élément</span><span class="sxs-lookup"><span data-stu-id="a549c-135">Element</span></span>|<span data-ttu-id="a549c-136">Description</span><span class="sxs-lookup"><span data-stu-id="a549c-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="a549c-137">Élément de liaison utilisé pour configurer des points de terminaison pour les services Web Windows Communication Foundation (WCF) qui répondent aux requêtes HTTP au lieu des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="a549c-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a549c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a549c-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="a549c-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a549c-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a549c-140">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="a549c-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a549c-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a549c-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a549c-142">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a549c-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a549c-143">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a549c-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="a549c-144">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="a549c-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
