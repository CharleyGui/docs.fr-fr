---
title: <transport> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 521aaf3913a1d30d10a674b71d4d98affcabc296
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399339"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="89eb2-102">\<> de transport \<de NetHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89eb2-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="89eb2-103">Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="89eb2-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="89eb2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89eb2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89eb2-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="89eb2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89eb2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="89eb2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="89eb2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="89eb2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="89eb2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="89eb2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="89eb2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="89eb2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="89eb2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="89eb2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89eb2-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89eb2-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89eb2-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89eb2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="89eb2-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89eb2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89eb2-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="89eb2-114">Attributes</span></span>  
  
|<span data-ttu-id="89eb2-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="89eb2-115">Attribute</span></span>|<span data-ttu-id="89eb2-116">Description</span><span class="sxs-lookup"><span data-stu-id="89eb2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89eb2-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="89eb2-117">clientCredentialType</span></span>|<span data-ttu-id="89eb2-118">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.</span><span class="sxs-lookup"><span data-stu-id="89eb2-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="89eb2-119">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="89eb2-119">The default is `None`.</span></span> <span data-ttu-id="89eb2-120">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="89eb2-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="89eb2-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="89eb2-121">proxyCredentialType</span></span>|<span data-ttu-id="89eb2-122">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="89eb2-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="89eb2-123">Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="89eb2-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="89eb2-124">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="89eb2-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="89eb2-125">realm</span><span class="sxs-lookup"><span data-stu-id="89eb2-125">realm</span></span>|<span data-ttu-id="89eb2-126">Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base.</span><span class="sxs-lookup"><span data-stu-id="89eb2-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="89eb2-127">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="89eb2-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="89eb2-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="89eb2-128">policyEnforcement</span></span>|<span data-ttu-id="89eb2-129">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="89eb2-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="89eb2-130">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="89eb2-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="89eb2-131">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="89eb2-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="89eb2-132">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="89eb2-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="89eb2-133">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="89eb2-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="89eb2-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="89eb2-134">protectionScenario</span></span>|<span data-ttu-id="89eb2-135">Cette énumération spécifie le scénario de protection appliqué par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="89eb2-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="89eb2-136">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="89eb2-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89eb2-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="89eb2-137">Value</span></span>|<span data-ttu-id="89eb2-138">Description</span><span class="sxs-lookup"><span data-stu-id="89eb2-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89eb2-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="89eb2-139">None</span></span>|<span data-ttu-id="89eb2-140">Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="89eb2-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89eb2-141">De base</span><span class="sxs-lookup"><span data-stu-id="89eb2-141">Basic</span></span>|<span data-ttu-id="89eb2-142">Spécifie l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="89eb2-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="89eb2-143">Digest</span><span class="sxs-lookup"><span data-stu-id="89eb2-143">Digest</span></span>|<span data-ttu-id="89eb2-144">Spécifie l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="89eb2-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="89eb2-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="89eb2-145">Ntlm</span></span>|<span data-ttu-id="89eb2-146">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="89eb2-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89eb2-147">Windows</span><span class="sxs-lookup"><span data-stu-id="89eb2-147">Windows</span></span>|<span data-ttu-id="89eb2-148">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="89eb2-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="89eb2-149">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="89eb2-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89eb2-150">`Value`</span><span class="sxs-lookup"><span data-stu-id="89eb2-150">Value</span></span>|<span data-ttu-id="89eb2-151">Description</span><span class="sxs-lookup"><span data-stu-id="89eb2-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89eb2-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="89eb2-152">None</span></span>|<span data-ttu-id="89eb2-153">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="89eb2-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89eb2-154">De base</span><span class="sxs-lookup"><span data-stu-id="89eb2-154">Basic</span></span>|<span data-ttu-id="89eb2-155">Spécifie l’authentification de base telle que définie par RFC 2617 – authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="89eb2-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89eb2-156">Digest</span><span class="sxs-lookup"><span data-stu-id="89eb2-156">Digest</span></span>|<span data-ttu-id="89eb2-157">Spécifie l’authentification Digest telle que définie par RFC 2617 – authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="89eb2-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89eb2-158">Ntlm</span><span class="sxs-lookup"><span data-stu-id="89eb2-158">Ntlm</span></span>|<span data-ttu-id="89eb2-159">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="89eb2-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89eb2-160">Windows</span><span class="sxs-lookup"><span data-stu-id="89eb2-160">Windows</span></span>|<span data-ttu-id="89eb2-161">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="89eb2-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="89eb2-162">Certificat</span><span class="sxs-lookup"><span data-stu-id="89eb2-162">Certificate</span></span>|<span data-ttu-id="89eb2-163">Effectue l'authentification du client à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="89eb2-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="89eb2-164">Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="89eb2-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89eb2-165">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89eb2-165">Child Elements</span></span>  
 <span data-ttu-id="89eb2-166">Aucun</span><span class="sxs-lookup"><span data-stu-id="89eb2-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89eb2-167">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89eb2-167">Parent Elements</span></span>  
  
|<span data-ttu-id="89eb2-168">Élément</span><span class="sxs-lookup"><span data-stu-id="89eb2-168">Element</span></span>|<span data-ttu-id="89eb2-169">Description</span><span class="sxs-lookup"><span data-stu-id="89eb2-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89eb2-170">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="89eb2-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="89eb2-171">Définit les fonctionnalités de sécurité pour le [ \<> NetHttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="89eb2-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89eb2-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="89eb2-172">Example</span></span>  
 <span data-ttu-id="89eb2-173">L'exemple suivant montre l'utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="89eb2-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="89eb2-174">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="89eb2-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89eb2-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89eb2-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="89eb2-176">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="89eb2-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="89eb2-177">Liaisons</span><span class="sxs-lookup"><span data-stu-id="89eb2-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="89eb2-178">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="89eb2-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="89eb2-179">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="89eb2-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="89eb2-180">\<binding></span><span class="sxs-lookup"><span data-stu-id="89eb2-180">\<binding></span></span>](../../../misc/binding.md)
