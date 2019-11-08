---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735933"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="5dc50-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="5dc50-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="5dc50-103">Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec le [\<NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5dc50-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="5dc50-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5dc50-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5dc50-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5dc50-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5dc50-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="5dc50-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="5dc50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetTcpBinding**](nettcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="5dc50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="5dc50-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="5dc50-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="5dc50-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-nettcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="5dc50-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="5dc50-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="5dc50-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dc50-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dc50-111">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dc50-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5dc50-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5dc50-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5dc50-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dc50-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5dc50-114">Attributes</span></span>  
  
|<span data-ttu-id="5dc50-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="5dc50-115">Attribute</span></span>|<span data-ttu-id="5dc50-116">Description</span><span class="sxs-lookup"><span data-stu-id="5dc50-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5dc50-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5dc50-117">clientCredentialType</span></span>|<span data-ttu-id="5dc50-118">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5dc50-118">Optional.</span></span> <span data-ttu-id="5dc50-119">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="5dc50-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="5dc50-120">-La valeur par défaut est `Windows`.</span><span class="sxs-lookup"><span data-stu-id="5dc50-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="5dc50-121">-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5dc50-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="5dc50-122">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5dc50-122">protectionLevel</span></span>|<span data-ttu-id="5dc50-123">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5dc50-123">Optional.</span></span> <span data-ttu-id="5dc50-124">Définit la sécurité au niveau du transport TCP.</span><span class="sxs-lookup"><span data-stu-id="5dc50-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="5dc50-125">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="5dc50-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5dc50-126">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="5dc50-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="5dc50-127">La valeur par défaut est `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="5dc50-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="5dc50-128">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5dc50-128">sslProtocols</span></span>|<span data-ttu-id="5dc50-129">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5dc50-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5dc50-130">La valeur par défaut&#124;est&#124;TLS Tls11 Tls12.</span><span class="sxs-lookup"><span data-stu-id="5dc50-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="5dc50-131">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="5dc50-131">policyEnforcement</span></span>|<span data-ttu-id="5dc50-132">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="5dc50-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5dc50-133">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="5dc50-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5dc50-134">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="5dc50-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5dc50-135">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="5dc50-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5dc50-136">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="5dc50-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5dc50-137">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5dc50-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5dc50-138">valeur</span><span class="sxs-lookup"><span data-stu-id="5dc50-138">Value</span></span>|<span data-ttu-id="5dc50-139">Description</span><span class="sxs-lookup"><span data-stu-id="5dc50-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5dc50-140">aucune.</span><span class="sxs-lookup"><span data-stu-id="5dc50-140">None</span></span>|<span data-ttu-id="5dc50-141">Le client est anonyme.</span><span class="sxs-lookup"><span data-stu-id="5dc50-141">The client is anonymous.</span></span> <span data-ttu-id="5dc50-142">Cela requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="5dc50-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="5dc50-143">Windows</span><span class="sxs-lookup"><span data-stu-id="5dc50-143">Windows</span></span>|<span data-ttu-id="5dc50-144">Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).</span><span class="sxs-lookup"><span data-stu-id="5dc50-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="5dc50-145">Certificat</span><span class="sxs-lookup"><span data-stu-id="5dc50-145">Certificate</span></span>|<span data-ttu-id="5dc50-146">Le client est authentifié à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="5dc50-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="5dc50-147">Cette valeur utilise la négociation SSL et requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="5dc50-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="5dc50-148">protectionLevel, attribut</span><span class="sxs-lookup"><span data-stu-id="5dc50-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="5dc50-149">valeur</span><span class="sxs-lookup"><span data-stu-id="5dc50-149">Value</span></span>|<span data-ttu-id="5dc50-150">Description</span><span class="sxs-lookup"><span data-stu-id="5dc50-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5dc50-151">aucune.</span><span class="sxs-lookup"><span data-stu-id="5dc50-151">None</span></span>|<span data-ttu-id="5dc50-152">Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="5dc50-152">No protection.</span></span>|  
|<span data-ttu-id="5dc50-153">Sign</span><span class="sxs-lookup"><span data-stu-id="5dc50-153">Sign</span></span>|<span data-ttu-id="5dc50-154">Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="5dc50-154">Messages are signed.</span></span>|  
|<span data-ttu-id="5dc50-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="5dc50-155">EncryptAndSign</span></span>|<span data-ttu-id="5dc50-156">-Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="5dc50-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dc50-157">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5dc50-157">Child Elements</span></span>  
 <span data-ttu-id="5dc50-158">aucune.</span><span class="sxs-lookup"><span data-stu-id="5dc50-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dc50-159">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5dc50-159">Parent Elements</span></span>  
  
|<span data-ttu-id="5dc50-160">Élément</span><span class="sxs-lookup"><span data-stu-id="5dc50-160">Element</span></span>|<span data-ttu-id="5dc50-161">Description</span><span class="sxs-lookup"><span data-stu-id="5dc50-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dc50-162">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="5dc50-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="5dc50-163">Spécifie les fonctionnalités de sécurité de la [\<NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5dc50-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dc50-164">Notes</span><span class="sxs-lookup"><span data-stu-id="5dc50-164">Remarks</span></span>  
 <span data-ttu-id="5dc50-165">Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle.</span><span class="sxs-lookup"><span data-stu-id="5dc50-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="5dc50-166">Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l'aide d'un transport sécurisé et les messages SOAP sont sécurisés à l'aide d'une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.</span><span class="sxs-lookup"><span data-stu-id="5dc50-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc50-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dc50-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="5dc50-168">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="5dc50-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5dc50-169">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5dc50-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5dc50-170">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="5dc50-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5dc50-171">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="5dc50-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5dc50-172">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="5dc50-172">\<binding></span></span>](bindings.md)
