---
title: <transport> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732811"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="e17df-102">\<transport> de \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e17df-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="e17df-103">Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="e17df-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="e17df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e17df-104">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e17df-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e17df-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e17df-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e17df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e17df-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e17df-107">Attributes</span></span>  
  
|<span data-ttu-id="e17df-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e17df-108">Attribute</span></span>|<span data-ttu-id="e17df-109">Description</span><span class="sxs-lookup"><span data-stu-id="e17df-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e17df-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e17df-110">clientCredentialType</span></span>|<span data-ttu-id="e17df-111">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.</span><span class="sxs-lookup"><span data-stu-id="e17df-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="e17df-112">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="e17df-112">The default is `None`.</span></span> <span data-ttu-id="e17df-113">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e17df-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="e17df-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="e17df-114">proxyCredentialType</span></span>|<span data-ttu-id="e17df-115">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="e17df-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="e17df-116">Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="e17df-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="e17df-117">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e17df-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="e17df-118">realm</span><span class="sxs-lookup"><span data-stu-id="e17df-118">realm</span></span>|<span data-ttu-id="e17df-119">Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base.</span><span class="sxs-lookup"><span data-stu-id="e17df-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="e17df-120">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="e17df-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="e17df-121">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="e17df-121">policyEnforcement</span></span>|<span data-ttu-id="e17df-122">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="e17df-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e17df-123">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="e17df-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e17df-124">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="e17df-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e17df-125">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="e17df-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e17df-126">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="e17df-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="e17df-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="e17df-127">protectionScenario</span></span>|<span data-ttu-id="e17df-128">Cette énumération spécifie le scénario de protection appliqué par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="e17df-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e17df-129">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e17df-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e17df-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="e17df-130">Value</span></span>|<span data-ttu-id="e17df-131">Description</span><span class="sxs-lookup"><span data-stu-id="e17df-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e17df-132">None</span><span class="sxs-lookup"><span data-stu-id="e17df-132">None</span></span>|<span data-ttu-id="e17df-133">Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="e17df-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="e17df-134">De base</span><span class="sxs-lookup"><span data-stu-id="e17df-134">Basic</span></span>|<span data-ttu-id="e17df-135">Spécifie l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="e17df-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="e17df-136">Digest</span><span class="sxs-lookup"><span data-stu-id="e17df-136">Digest</span></span>|<span data-ttu-id="e17df-137">Spécifie l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="e17df-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="e17df-138">Ntlm</span><span class="sxs-lookup"><span data-stu-id="e17df-138">Ntlm</span></span>|<span data-ttu-id="e17df-139">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e17df-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="e17df-140">Windows</span><span class="sxs-lookup"><span data-stu-id="e17df-140">Windows</span></span>|<span data-ttu-id="e17df-141">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="e17df-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e17df-142">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="e17df-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e17df-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="e17df-143">Value</span></span>|<span data-ttu-id="e17df-144">Description</span><span class="sxs-lookup"><span data-stu-id="e17df-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e17df-145">None</span><span class="sxs-lookup"><span data-stu-id="e17df-145">None</span></span>|<span data-ttu-id="e17df-146">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="e17df-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="e17df-147">De base</span><span class="sxs-lookup"><span data-stu-id="e17df-147">Basic</span></span>|<span data-ttu-id="e17df-148">Spécifie l’authentification de base telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="e17df-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="e17df-149">Digest</span><span class="sxs-lookup"><span data-stu-id="e17df-149">Digest</span></span>|<span data-ttu-id="e17df-150">Spécifie l'authentification Digest telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="e17df-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="e17df-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="e17df-151">Ntlm</span></span>|<span data-ttu-id="e17df-152">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e17df-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="e17df-153">Windows</span><span class="sxs-lookup"><span data-stu-id="e17df-153">Windows</span></span>|<span data-ttu-id="e17df-154">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="e17df-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="e17df-155">Certificat</span><span class="sxs-lookup"><span data-stu-id="e17df-155">Certificate</span></span>|<span data-ttu-id="e17df-156">Effectue l'authentification du client à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="e17df-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="e17df-157">Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="e17df-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e17df-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e17df-158">Child Elements</span></span>  
 <span data-ttu-id="e17df-159">Aucune</span><span class="sxs-lookup"><span data-stu-id="e17df-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e17df-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e17df-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e17df-161">Élément</span><span class="sxs-lookup"><span data-stu-id="e17df-161">Element</span></span>|<span data-ttu-id="e17df-162">Description</span><span class="sxs-lookup"><span data-stu-id="e17df-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="e17df-163">Définit les fonctionnalités de sécurité pour [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e17df-163">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e17df-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="e17df-164">Example</span></span>  
 <span data-ttu-id="e17df-165">L'exemple suivant montre l'utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="e17df-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="e17df-166">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="e17df-166">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="e17df-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e17df-167">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="e17df-168">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="e17df-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e17df-169">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e17df-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e17df-170">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e17df-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e17df-171">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e17df-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
