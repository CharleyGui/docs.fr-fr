---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915546"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="e9489-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e9489-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="e9489-103">Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec le [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e9489-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="e9489-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e9489-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9489-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e9489-105">\<bindings></span></span>  
<span data-ttu-id="e9489-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e9489-106">\<netTcpBinding></span></span>  
<span data-ttu-id="e9489-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9489-107">\<binding></span></span>  
<span data-ttu-id="e9489-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="e9489-108">\<security></span></span>  
<span data-ttu-id="e9489-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="e9489-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9489-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9489-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9489-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e9489-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e9489-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e9489-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9489-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e9489-113">Attributes</span></span>  
  
|<span data-ttu-id="e9489-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e9489-114">Attribute</span></span>|<span data-ttu-id="e9489-115">Description</span><span class="sxs-lookup"><span data-stu-id="e9489-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9489-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e9489-116">clientCredentialType</span></span>|<span data-ttu-id="e9489-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e9489-117">Optional.</span></span> <span data-ttu-id="e9489-118">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="e9489-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="e9489-119">-La valeur par défaut `Windows`est.</span><span class="sxs-lookup"><span data-stu-id="e9489-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="e9489-120">-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e9489-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="e9489-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="e9489-121">protectionLevel</span></span>|<span data-ttu-id="e9489-122">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e9489-122">Optional.</span></span> <span data-ttu-id="e9489-123">Définit la sécurité au niveau du transport TCP.</span><span class="sxs-lookup"><span data-stu-id="e9489-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="e9489-124">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="e9489-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e9489-125">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="e9489-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="e9489-126">La valeur par défaut est `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="e9489-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="e9489-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="e9489-127">sslProtocols</span></span>|<span data-ttu-id="e9489-128">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e9489-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e9489-129">La valeur par défaut&#124;est&#124;TLS Tls11 Tls12.</span><span class="sxs-lookup"><span data-stu-id="e9489-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="e9489-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="e9489-130">policyEnforcement</span></span>|<span data-ttu-id="e9489-131">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="e9489-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e9489-132">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="e9489-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e9489-133">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="e9489-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e9489-134">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="e9489-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e9489-135">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="e9489-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e9489-136">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e9489-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e9489-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="e9489-137">Value</span></span>|<span data-ttu-id="e9489-138">Description</span><span class="sxs-lookup"><span data-stu-id="e9489-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9489-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="e9489-139">None</span></span>|<span data-ttu-id="e9489-140">Le client est anonyme.</span><span class="sxs-lookup"><span data-stu-id="e9489-140">The client is anonymous.</span></span> <span data-ttu-id="e9489-141">Cela requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="e9489-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="e9489-142">Windows</span><span class="sxs-lookup"><span data-stu-id="e9489-142">Windows</span></span>|<span data-ttu-id="e9489-143">Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).</span><span class="sxs-lookup"><span data-stu-id="e9489-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="e9489-144">Certificat</span><span class="sxs-lookup"><span data-stu-id="e9489-144">Certificate</span></span>|<span data-ttu-id="e9489-145">Le client est authentifié à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="e9489-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="e9489-146">Cette valeur utilise la négociation SSL et requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="e9489-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="e9489-147">protectionLevel, attribut</span><span class="sxs-lookup"><span data-stu-id="e9489-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="e9489-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="e9489-148">Value</span></span>|<span data-ttu-id="e9489-149">Description</span><span class="sxs-lookup"><span data-stu-id="e9489-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9489-150">Aucun</span><span class="sxs-lookup"><span data-stu-id="e9489-150">None</span></span>|<span data-ttu-id="e9489-151">Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="e9489-151">No protection.</span></span>|  
|<span data-ttu-id="e9489-152">Sign</span><span class="sxs-lookup"><span data-stu-id="e9489-152">Sign</span></span>|<span data-ttu-id="e9489-153">Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="e9489-153">Messages are signed.</span></span>|  
|<span data-ttu-id="e9489-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="e9489-154">EncryptAndSign</span></span>|<span data-ttu-id="e9489-155">-Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="e9489-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9489-156">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9489-156">Child Elements</span></span>  
 <span data-ttu-id="e9489-157">Aucun</span><span class="sxs-lookup"><span data-stu-id="e9489-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9489-158">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9489-158">Parent Elements</span></span>  
  
|<span data-ttu-id="e9489-159">Élément</span><span class="sxs-lookup"><span data-stu-id="e9489-159">Element</span></span>|<span data-ttu-id="e9489-160">Description</span><span class="sxs-lookup"><span data-stu-id="e9489-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9489-161">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="e9489-161">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="e9489-162">Spécifie les fonctionnalités de sécurité de la [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e9489-162">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9489-163">Notes</span><span class="sxs-lookup"><span data-stu-id="e9489-163">Remarks</span></span>  
 <span data-ttu-id="e9489-164">Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle.</span><span class="sxs-lookup"><span data-stu-id="e9489-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="e9489-165">Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l'aide d'un transport sécurisé et les messages SOAP sont sécurisés à l'aide d'une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.</span><span class="sxs-lookup"><span data-stu-id="e9489-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9489-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9489-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="e9489-167">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e9489-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9489-168">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e9489-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9489-169">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e9489-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9489-170">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e9489-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e9489-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9489-171">\<binding></span></span>](../../../misc/binding.md)
