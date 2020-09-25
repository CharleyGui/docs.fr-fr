---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: 48b49bf69f791f90ed5b2eea8e6d412438cd9519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169841"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="80540-102">\<security> de \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="80540-102">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="80540-103">Représente les paramètres de sécurité utilisés avec l' [\<ws2007HttpBinding>](ws2007httpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="80540-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="80540-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80540-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80540-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="80540-105">Attributes and Elements</span></span>  

 <span data-ttu-id="80540-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="80540-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80540-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="80540-107">Attributes</span></span>  
  
|<span data-ttu-id="80540-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="80540-108">Attribute</span></span>|<span data-ttu-id="80540-109">Description</span><span class="sxs-lookup"><span data-stu-id="80540-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="80540-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="80540-110">-   Optional.</span></span> <span data-ttu-id="80540-111">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="80540-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="80540-112">Par défaut, il s’agit de `Message`.</span><span class="sxs-lookup"><span data-stu-id="80540-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="80540-113">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="80540-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="80540-114">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="80540-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="80540-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="80540-115">Value</span></span>|<span data-ttu-id="80540-116">Description</span><span class="sxs-lookup"><span data-stu-id="80540-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="80540-117">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="80540-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="80540-118">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80540-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="80540-119">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="80540-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="80540-120">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="80540-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="80540-121">L’authentification du client est contrôlée par le biais `ClientCredentials` de l’attribut de l' [\<transport>](transport-of-ws2007httpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="80540-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="80540-122">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="80540-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="80540-123">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="80540-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="80540-124">Ce mode offre diverses fonctionnalités : déterminer si les informations d'identification du service sont disponibles pour le client hors bande, quelle est la suite algorithmique à utiliser et quel niveau de protection est à appliquer au corps du message via le <xref:System.ServiceModel.Security.SecurityMessageProperty>, entre autres.</span><span class="sxs-lookup"><span data-stu-id="80540-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="80540-125">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="80540-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="80540-126">Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="80540-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="80540-127">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="80540-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80540-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="80540-128">Child Elements</span></span>  
  
|<span data-ttu-id="80540-129">Élément</span><span class="sxs-lookup"><span data-stu-id="80540-129">Element</span></span>|<span data-ttu-id="80540-130">Description</span><span class="sxs-lookup"><span data-stu-id="80540-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="80540-131">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="80540-131">Defines the transport security settings.</span></span> <span data-ttu-id="80540-132">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="80540-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="80540-133">Ces paramètres sont appliqués uniquement lorsque le mode a la valeur Transport.</span><span class="sxs-lookup"><span data-stu-id="80540-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="80540-134">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="80540-134">Defines the security settings for the message.</span></span> <span data-ttu-id="80540-135">Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="80540-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="80540-136">Ces paramètres ne sont pas appliqués lorsque le mode a la valeur Transport.</span><span class="sxs-lookup"><span data-stu-id="80540-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80540-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="80540-137">Parent Elements</span></span>  
  
|<span data-ttu-id="80540-138">Élément</span><span class="sxs-lookup"><span data-stu-id="80540-138">Element</span></span>|<span data-ttu-id="80540-139">Description</span><span class="sxs-lookup"><span data-stu-id="80540-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="80540-140">Liaison sécurisée pour les applications de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="80540-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80540-141">Notes</span><span class="sxs-lookup"><span data-stu-id="80540-141">Remarks</span></span>  

 <span data-ttu-id="80540-142">Cet élément est conçu pour interagir avec les services qui implémentent les spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="80540-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="80540-143">La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80540-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80540-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80540-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="80540-145">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="80540-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="80540-146">Liaisons</span><span class="sxs-lookup"><span data-stu-id="80540-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="80540-147">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="80540-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="80540-148">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="80540-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
