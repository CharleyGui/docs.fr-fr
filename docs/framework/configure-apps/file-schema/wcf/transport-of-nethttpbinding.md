---
title: <transport> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732811"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="daec1-102">\<> de transport de \<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="daec1-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="daec1-103">Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="daec1-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="daec1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="daec1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="daec1-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="daec1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="daec1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="daec1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="daec1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetHttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="daec1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="daec1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="daec1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="daec1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="daec1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="daec1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="daec1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daec1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daec1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="daec1-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="daec1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="daec1-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="daec1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="daec1-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="daec1-114">Attributes</span></span>  
  
|<span data-ttu-id="daec1-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="daec1-115">Attribute</span></span>|<span data-ttu-id="daec1-116">Description</span><span class="sxs-lookup"><span data-stu-id="daec1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="daec1-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="daec1-117">clientCredentialType</span></span>|<span data-ttu-id="daec1-118">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.</span><span class="sxs-lookup"><span data-stu-id="daec1-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="daec1-119">La valeur par défaut est `None`,</span><span class="sxs-lookup"><span data-stu-id="daec1-119">The default is `None`.</span></span> <span data-ttu-id="daec1-120">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="daec1-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="daec1-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="daec1-121">proxyCredentialType</span></span>|<span data-ttu-id="daec1-122">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="daec1-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="daec1-123">Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="daec1-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="daec1-124">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="daec1-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="daec1-125">realm</span><span class="sxs-lookup"><span data-stu-id="daec1-125">realm</span></span>|<span data-ttu-id="daec1-126">Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base.</span><span class="sxs-lookup"><span data-stu-id="daec1-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="daec1-127">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="daec1-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="daec1-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="daec1-128">policyEnforcement</span></span>|<span data-ttu-id="daec1-129">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="daec1-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="daec1-130">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="daec1-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="daec1-131">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="daec1-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="daec1-132">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="daec1-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="daec1-133">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="daec1-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="daec1-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="daec1-134">protectionScenario</span></span>|<span data-ttu-id="daec1-135">Cette énumération spécifie le scénario de protection appliqué par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="daec1-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="daec1-136">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="daec1-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="daec1-137">valeur</span><span class="sxs-lookup"><span data-stu-id="daec1-137">Value</span></span>|<span data-ttu-id="daec1-138">Description</span><span class="sxs-lookup"><span data-stu-id="daec1-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="daec1-139">aucune.</span><span class="sxs-lookup"><span data-stu-id="daec1-139">None</span></span>|<span data-ttu-id="daec1-140">Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="daec1-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="daec1-141">Basic</span><span class="sxs-lookup"><span data-stu-id="daec1-141">Basic</span></span>|<span data-ttu-id="daec1-142">Spécifie l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="daec1-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="daec1-143">Digest</span><span class="sxs-lookup"><span data-stu-id="daec1-143">Digest</span></span>|<span data-ttu-id="daec1-144">Spécifie l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="daec1-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="daec1-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="daec1-145">Ntlm</span></span>|<span data-ttu-id="daec1-146">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="daec1-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="daec1-147">Windows</span><span class="sxs-lookup"><span data-stu-id="daec1-147">Windows</span></span>|<span data-ttu-id="daec1-148">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="daec1-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="daec1-149">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="daec1-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="daec1-150">valeur</span><span class="sxs-lookup"><span data-stu-id="daec1-150">Value</span></span>|<span data-ttu-id="daec1-151">Description</span><span class="sxs-lookup"><span data-stu-id="daec1-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="daec1-152">aucune.</span><span class="sxs-lookup"><span data-stu-id="daec1-152">None</span></span>|<span data-ttu-id="daec1-153">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="daec1-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="daec1-154">Basic</span><span class="sxs-lookup"><span data-stu-id="daec1-154">Basic</span></span>|<span data-ttu-id="daec1-155">Spécifie l’authentification de base telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="daec1-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="daec1-156">Digest</span><span class="sxs-lookup"><span data-stu-id="daec1-156">Digest</span></span>|<span data-ttu-id="daec1-157">Spécifie l'authentification Digest telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="daec1-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="daec1-158">Ntlm</span><span class="sxs-lookup"><span data-stu-id="daec1-158">Ntlm</span></span>|<span data-ttu-id="daec1-159">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="daec1-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="daec1-160">Windows</span><span class="sxs-lookup"><span data-stu-id="daec1-160">Windows</span></span>|<span data-ttu-id="daec1-161">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="daec1-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="daec1-162">Certificat</span><span class="sxs-lookup"><span data-stu-id="daec1-162">Certificate</span></span>|<span data-ttu-id="daec1-163">Effectue l'authentification du client à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="daec1-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="daec1-164">Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="daec1-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="daec1-165">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="daec1-165">Child Elements</span></span>  
 <span data-ttu-id="daec1-166">aucune.</span><span class="sxs-lookup"><span data-stu-id="daec1-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="daec1-167">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="daec1-167">Parent Elements</span></span>  
  
|<span data-ttu-id="daec1-168">Élément</span><span class="sxs-lookup"><span data-stu-id="daec1-168">Element</span></span>|<span data-ttu-id="daec1-169">Description</span><span class="sxs-lookup"><span data-stu-id="daec1-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daec1-170">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="daec1-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="daec1-171">Définit les fonctionnalités de sécurité pour le [\<NetHttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="daec1-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="daec1-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="daec1-172">Example</span></span>  
 <span data-ttu-id="daec1-173">L'exemple suivant montre l'utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="daec1-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="daec1-174">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="daec1-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="daec1-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daec1-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="daec1-176">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="daec1-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="daec1-177">Liaisons</span><span class="sxs-lookup"><span data-stu-id="daec1-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="daec1-178">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="daec1-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="daec1-179">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="daec1-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="daec1-180">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="daec1-180">\<binding></span></span>](bindings.md)
