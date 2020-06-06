---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735933"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="f25b0-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f25b0-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="f25b0-103">Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec le [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f25b0-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="f25b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f25b0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f25b0-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f25b0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f25b0-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f25b0-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f25b0-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f25b0-107">Attributes</span></span>  
  
|<span data-ttu-id="f25b0-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f25b0-108">Attribute</span></span>|<span data-ttu-id="f25b0-109">Description</span><span class="sxs-lookup"><span data-stu-id="f25b0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f25b0-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f25b0-110">clientCredentialType</span></span>|<span data-ttu-id="f25b0-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f25b0-111">Optional.</span></span> <span data-ttu-id="f25b0-112">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="f25b0-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="f25b0-113">-La valeur par défaut est `Windows` .</span><span class="sxs-lookup"><span data-stu-id="f25b0-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="f25b0-114">-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="f25b0-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="f25b0-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="f25b0-115">protectionLevel</span></span>|<span data-ttu-id="f25b0-116">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f25b0-116">Optional.</span></span> <span data-ttu-id="f25b0-117">Définit la sécurité au niveau du transport TCP.</span><span class="sxs-lookup"><span data-stu-id="f25b0-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="f25b0-118">La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert.</span><span class="sxs-lookup"><span data-stu-id="f25b0-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="f25b0-119">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="f25b0-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="f25b0-120">La valeur par défaut est `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="f25b0-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="f25b0-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="f25b0-121">sslProtocols</span></span>|<span data-ttu-id="f25b0-122">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f25b0-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="f25b0-123">La valeur par défaut est TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="f25b0-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="f25b0-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="f25b0-124">policyEnforcement</span></span>|<span data-ttu-id="f25b0-125">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="f25b0-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="f25b0-126">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="f25b0-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="f25b0-127">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="f25b0-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="f25b0-128">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="f25b0-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="f25b0-129">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="f25b0-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f25b0-130">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f25b0-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f25b0-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="f25b0-131">Value</span></span>|<span data-ttu-id="f25b0-132">Description</span><span class="sxs-lookup"><span data-stu-id="f25b0-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f25b0-133">None</span><span class="sxs-lookup"><span data-stu-id="f25b0-133">None</span></span>|<span data-ttu-id="f25b0-134">Le client est anonyme.</span><span class="sxs-lookup"><span data-stu-id="f25b0-134">The client is anonymous.</span></span> <span data-ttu-id="f25b0-135">Cela requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="f25b0-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="f25b0-136">Windows</span><span class="sxs-lookup"><span data-stu-id="f25b0-136">Windows</span></span>|<span data-ttu-id="f25b0-137">Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).</span><span class="sxs-lookup"><span data-stu-id="f25b0-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="f25b0-138">Certificat</span><span class="sxs-lookup"><span data-stu-id="f25b0-138">Certificate</span></span>|<span data-ttu-id="f25b0-139">Le client est authentifié à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="f25b0-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="f25b0-140">Cette valeur utilise la négociation SSL et requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="f25b0-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="f25b0-141">protectionLevel, attribut</span><span class="sxs-lookup"><span data-stu-id="f25b0-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="f25b0-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="f25b0-142">Value</span></span>|<span data-ttu-id="f25b0-143">Description</span><span class="sxs-lookup"><span data-stu-id="f25b0-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f25b0-144">None</span><span class="sxs-lookup"><span data-stu-id="f25b0-144">None</span></span>|<span data-ttu-id="f25b0-145">Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="f25b0-145">No protection.</span></span>|  
|<span data-ttu-id="f25b0-146">Signer</span><span class="sxs-lookup"><span data-stu-id="f25b0-146">Sign</span></span>|<span data-ttu-id="f25b0-147">Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="f25b0-147">Messages are signed.</span></span>|  
|<span data-ttu-id="f25b0-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="f25b0-148">EncryptAndSign</span></span>|<span data-ttu-id="f25b0-149">-Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="f25b0-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f25b0-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f25b0-150">Child Elements</span></span>  
 <span data-ttu-id="f25b0-151">Aucune</span><span class="sxs-lookup"><span data-stu-id="f25b0-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f25b0-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f25b0-152">Parent Elements</span></span>  
  
|<span data-ttu-id="f25b0-153">Élément</span><span class="sxs-lookup"><span data-stu-id="f25b0-153">Element</span></span>|<span data-ttu-id="f25b0-154">Description</span><span class="sxs-lookup"><span data-stu-id="f25b0-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="f25b0-155">Spécifie les fonctionnalités de sécurité de [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f25b0-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f25b0-156">Remarques</span><span class="sxs-lookup"><span data-stu-id="f25b0-156">Remarks</span></span>  
 <span data-ttu-id="f25b0-157">Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle.</span><span class="sxs-lookup"><span data-stu-id="f25b0-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="f25b0-158">Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l'aide d'un transport sécurisé et les messages SOAP sont sécurisés à l'aide d'une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.</span><span class="sxs-lookup"><span data-stu-id="f25b0-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25b0-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f25b0-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="f25b0-160">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="f25b0-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f25b0-161">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f25b0-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f25b0-162">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f25b0-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f25b0-163">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f25b0-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
