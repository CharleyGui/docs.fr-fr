---
title: <security> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: d39e3e5e655817aa91c5301274a860a00a6ab7ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169984"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="228b1-102">\<security> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="228b1-102">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="228b1-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="228b1-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="228b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="228b1-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="228b1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="228b1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="228b1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="228b1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="228b1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="228b1-107">Attributes</span></span>  
  
|<span data-ttu-id="228b1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="228b1-108">Attribute</span></span>|<span data-ttu-id="228b1-109">Description</span><span class="sxs-lookup"><span data-stu-id="228b1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="228b1-110">mode</span><span class="sxs-lookup"><span data-stu-id="228b1-110">mode</span></span>|<span data-ttu-id="228b1-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="228b1-111">Optional.</span></span> <span data-ttu-id="228b1-112">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="228b1-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="228b1-113">Les valeurs autorisées sont présentées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="228b1-113">Valid values are shown below.</span></span> <span data-ttu-id="228b1-114">La valeur par défaut est `Transport`.</span><span class="sxs-lookup"><span data-stu-id="228b1-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="228b1-115">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="228b1-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="228b1-116">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="228b1-116">mode Attribute</span></span>  
  
|<span data-ttu-id="228b1-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="228b1-117">Value</span></span>|<span data-ttu-id="228b1-118">Description</span><span class="sxs-lookup"><span data-stu-id="228b1-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="228b1-119">None</span><span class="sxs-lookup"><span data-stu-id="228b1-119">None</span></span>|<span data-ttu-id="228b1-120">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="228b1-120">Security is disabled.</span></span>|  
|<span data-ttu-id="228b1-121">Transport</span><span class="sxs-lookup"><span data-stu-id="228b1-121">Transport</span></span>|<span data-ttu-id="228b1-122">La sécurité de transport est fournie à l'aide du TLS sur le TCP ou SPNego.</span><span class="sxs-lookup"><span data-stu-id="228b1-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="228b1-123">Le service peut devoir être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="228b1-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="228b1-124">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="228b1-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="228b1-125">Message</span><span class="sxs-lookup"><span data-stu-id="228b1-125">Message</span></span>|<span data-ttu-id="228b1-126">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="228b1-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="228b1-127">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="228b1-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="228b1-128">Ce mode offre diverses fonctionnalités, telles que, si les informations d'identification du service sont disponibles pour le client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message.</span><span class="sxs-lookup"><span data-stu-id="228b1-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="228b1-129">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="228b1-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="228b1-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="228b1-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="228b1-131">La sécurité de transport est associée à la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="228b1-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="228b1-132">La sécurité de transport est fournie par le TLS sur le TCP ou SPNego, et garantit l'intégrité, la confidentialité et l'authentification du serveur.</span><span class="sxs-lookup"><span data-stu-id="228b1-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="228b1-133">La sécurité des messages SOAP fournit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="228b1-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="228b1-134">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="228b1-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="228b1-135">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="228b1-135">Child Elements</span></span>  
  
|<span data-ttu-id="228b1-136">Élément</span><span class="sxs-lookup"><span data-stu-id="228b1-136">Element</span></span>|<span data-ttu-id="228b1-137">Description</span><span class="sxs-lookup"><span data-stu-id="228b1-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="228b1-138">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="228b1-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="228b1-139">Cet élément est de type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="228b1-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="228b1-140">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="228b1-140">Defines the security settings for the message.</span></span> <span data-ttu-id="228b1-141">Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="228b1-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="228b1-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="228b1-142">Parent Elements</span></span>  
  
|<span data-ttu-id="228b1-143">Élément</span><span class="sxs-lookup"><span data-stu-id="228b1-143">Element</span></span>|<span data-ttu-id="228b1-144">Description</span><span class="sxs-lookup"><span data-stu-id="228b1-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="228b1-145">binding</span><span class="sxs-lookup"><span data-stu-id="228b1-145">binding</span></span>|<span data-ttu-id="228b1-146">Élément de liaison de [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="228b1-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228b1-147">Notes</span><span class="sxs-lookup"><span data-stu-id="228b1-147">Remarks</span></span>  

 <span data-ttu-id="228b1-148">Chaque liaison standard fournit des paramètres pour le contrôle des conditions de sécurité de transfert.</span><span class="sxs-lookup"><span data-stu-id="228b1-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="228b1-149">Ces paramètres incluent généralement le mode de sécurité qui indique si la sécurité au niveau du message ou du transport est utilisée et le choix du type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="228b1-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="228b1-150">Selon le choix d'options présentées par ces paramètres, une pile de canaux est construite avec la sécurité appropriée.</span><span class="sxs-lookup"><span data-stu-id="228b1-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="228b1-151">Les liaisons fournies par le système par Windows Communication Foundation (WCF) constituent un ensemble conçu pour satisfaire aux exigences de scénario les plus courants.</span><span class="sxs-lookup"><span data-stu-id="228b1-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="228b1-152">Chaque liaison permet la spécification des conditions de sécurité pour des scénarios spécifiques.</span><span class="sxs-lookup"><span data-stu-id="228b1-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="228b1-153">Cet élément de configuration fournit les caractéristiques de sécurité pour `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="228b1-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="228b1-154">Il s’agit d’une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="228b1-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="228b1-155">Par défaut, elle génère une pile de communication d'exécution prenant en charge le TCP pour la remise des messages, Windows Security pour l'authentification et la sécurité des messages, WS-ReliableMessaging pour la fiabilité et l'encodage de messages binaires.</span><span class="sxs-lookup"><span data-stu-id="228b1-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228b1-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="228b1-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="228b1-157">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="228b1-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="228b1-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="228b1-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="228b1-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="228b1-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="228b1-160">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="228b1-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
