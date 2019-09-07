---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399789"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="b8540-102">\<> de sécurité \<de WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b8540-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="b8540-103">Représente les paramètres de sécurité utilisés avec l' [ \<élément WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b8540-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="b8540-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8540-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8540-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b8540-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b8540-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b8540-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b8540-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b8540-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="b8540-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="b8540-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b8540-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="b8540-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8540-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8540-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8540-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8540-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b8540-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8540-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8540-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8540-113">Attributes</span></span>  
  
|<span data-ttu-id="b8540-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="b8540-114">Attribute</span></span>|<span data-ttu-id="b8540-115">Description</span><span class="sxs-lookup"><span data-stu-id="b8540-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="b8540-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b8540-116">-   Optional.</span></span> <span data-ttu-id="b8540-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="b8540-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b8540-118">Par défaut, il s’agit de `Message`.</span><span class="sxs-lookup"><span data-stu-id="b8540-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="b8540-119">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b8540-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b8540-120">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="b8540-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="b8540-121">`Value`</span><span class="sxs-lookup"><span data-stu-id="b8540-121">Value</span></span>|<span data-ttu-id="b8540-122">Description</span><span class="sxs-lookup"><span data-stu-id="b8540-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b8540-123">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b8540-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="b8540-124">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b8540-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="b8540-125">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="b8540-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="b8540-126">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="b8540-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="b8540-127">L’authentification du client est contrôlée par `ClientCredentials` le biais de l’attribut de l' [ \<](transport-of-ws2007httpbinding.md) élément de > de transport.</span><span class="sxs-lookup"><span data-stu-id="b8540-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="b8540-128">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="b8540-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="b8540-129">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="b8540-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="b8540-130">Ce mode offre diverses fonctionnalités : déterminer si les informations d'identification du service sont disponibles pour le client hors bande, quelle est la suite algorithmique à utiliser et quel niveau de protection est à appliquer au corps du message via le <xref:System.ServiceModel.Security.SecurityMessageProperty>, entre autres.</span><span class="sxs-lookup"><span data-stu-id="b8540-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="b8540-131">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="b8540-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="b8540-132">Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="b8540-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="b8540-133">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="b8540-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8540-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8540-134">Child Elements</span></span>  
  
|<span data-ttu-id="b8540-135">Élément</span><span class="sxs-lookup"><span data-stu-id="b8540-135">Element</span></span>|<span data-ttu-id="b8540-136">Description</span><span class="sxs-lookup"><span data-stu-id="b8540-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8540-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="b8540-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="b8540-138">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="b8540-138">Defines the transport security settings.</span></span> <span data-ttu-id="b8540-139">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b8540-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="b8540-140">Ces paramètres sont appliqués uniquement lorsque le mode a la valeur Transport.</span><span class="sxs-lookup"><span data-stu-id="b8540-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="b8540-141">\<message></span><span class="sxs-lookup"><span data-stu-id="b8540-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="b8540-142">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="b8540-142">Defines the security settings for the message.</span></span> <span data-ttu-id="b8540-143">Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="b8540-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="b8540-144">Ces paramètres ne sont pas appliqués lorsque le mode a la valeur Transport.</span><span class="sxs-lookup"><span data-stu-id="b8540-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8540-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8540-145">Parent Elements</span></span>  
  
|<span data-ttu-id="b8540-146">Élément</span><span class="sxs-lookup"><span data-stu-id="b8540-146">Element</span></span>|<span data-ttu-id="b8540-147">Description</span><span class="sxs-lookup"><span data-stu-id="b8540-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8540-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="b8540-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="b8540-149">Liaison sécurisée pour les applications de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="b8540-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8540-150">Notes</span><span class="sxs-lookup"><span data-stu-id="b8540-150">Remarks</span></span>  
 <span data-ttu-id="b8540-151">Cet élément est conçu pour interagir avec les services qui implémentent les spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="b8540-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="b8540-152">La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b8540-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8540-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8540-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b8540-154">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b8540-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b8540-155">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b8540-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b8540-156">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="b8540-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b8540-157">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b8540-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b8540-158">\<binding></span><span class="sxs-lookup"><span data-stu-id="b8540-158">\<binding></span></span>](../../../misc/binding.md)
