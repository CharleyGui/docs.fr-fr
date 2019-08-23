---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: af5852c3c7850f91686d50294c8846f85574e909
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918632"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="de1da-102">\<> de transport \<de BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="de1da-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="de1da-103">Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="de1da-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="de1da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de1da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de1da-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="de1da-105">\<bindings></span></span>  
<span data-ttu-id="de1da-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="de1da-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="de1da-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="de1da-107">\<binding></span></span>  
<span data-ttu-id="de1da-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="de1da-108">\<security></span></span>  
<span data-ttu-id="de1da-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="de1da-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1da-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de1da-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de1da-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de1da-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de1da-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de1da-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de1da-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="de1da-113">Attributes</span></span>  
  
|<span data-ttu-id="de1da-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="de1da-114">Attribute</span></span>|<span data-ttu-id="de1da-115">Description</span><span class="sxs-lookup"><span data-stu-id="de1da-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de1da-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="de1da-116">clientCredentialType</span></span>|<span data-ttu-id="de1da-117">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.</span><span class="sxs-lookup"><span data-stu-id="de1da-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="de1da-118">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="de1da-118">The default is `None`.</span></span> <span data-ttu-id="de1da-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="de1da-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="de1da-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="de1da-120">proxyCredentialType</span></span>|<span data-ttu-id="de1da-121">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="de1da-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="de1da-122">Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="de1da-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="de1da-123">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="de1da-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="de1da-124">realm</span><span class="sxs-lookup"><span data-stu-id="de1da-124">realm</span></span>|<span data-ttu-id="de1da-125">Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base.</span><span class="sxs-lookup"><span data-stu-id="de1da-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="de1da-126">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="de1da-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="de1da-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="de1da-127">policyEnforcement</span></span>|<span data-ttu-id="de1da-128">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="de1da-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="de1da-129">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="de1da-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="de1da-130">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="de1da-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="de1da-131">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="de1da-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="de1da-132">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="de1da-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="de1da-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="de1da-133">protectionScenario</span></span>|<span data-ttu-id="de1da-134">Cette énumération spécifie le scénario de protection appliqué par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="de1da-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="de1da-135">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="de1da-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="de1da-136">`Value`</span><span class="sxs-lookup"><span data-stu-id="de1da-136">Value</span></span>|<span data-ttu-id="de1da-137">Description</span><span class="sxs-lookup"><span data-stu-id="de1da-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de1da-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="de1da-138">None</span></span>|<span data-ttu-id="de1da-139">Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="de1da-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="de1da-140">De base</span><span class="sxs-lookup"><span data-stu-id="de1da-140">Basic</span></span>|<span data-ttu-id="de1da-141">Spécifie l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="de1da-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="de1da-142">Digest</span><span class="sxs-lookup"><span data-stu-id="de1da-142">Digest</span></span>|<span data-ttu-id="de1da-143">Spécifie l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="de1da-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="de1da-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="de1da-144">Ntlm</span></span>|<span data-ttu-id="de1da-145">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="de1da-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="de1da-146">Windows</span><span class="sxs-lookup"><span data-stu-id="de1da-146">Windows</span></span>|<span data-ttu-id="de1da-147">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="de1da-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="de1da-148">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="de1da-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="de1da-149">Valeur</span><span class="sxs-lookup"><span data-stu-id="de1da-149">Value</span></span>|<span data-ttu-id="de1da-150">Description</span><span class="sxs-lookup"><span data-stu-id="de1da-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de1da-151">Aucun</span><span class="sxs-lookup"><span data-stu-id="de1da-151">None</span></span>|<span data-ttu-id="de1da-152">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="de1da-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="de1da-153">De base</span><span class="sxs-lookup"><span data-stu-id="de1da-153">Basic</span></span>|<span data-ttu-id="de1da-154">Spécifie l’authentification de base telle que définie par RFC 2617 – authentification HTTP: Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="de1da-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="de1da-155">Digest</span><span class="sxs-lookup"><span data-stu-id="de1da-155">Digest</span></span>|<span data-ttu-id="de1da-156">Spécifie l’authentification Digest telle que définie par RFC 2617 – authentification HTTP: Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="de1da-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="de1da-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="de1da-157">Ntlm</span></span>|<span data-ttu-id="de1da-158">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="de1da-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="de1da-159">Windows</span><span class="sxs-lookup"><span data-stu-id="de1da-159">Windows</span></span>|<span data-ttu-id="de1da-160">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="de1da-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="de1da-161">Certificat</span><span class="sxs-lookup"><span data-stu-id="de1da-161">Certificate</span></span>|<span data-ttu-id="de1da-162">Effectue l'authentification du client à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="de1da-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="de1da-163">Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="de1da-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de1da-164">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de1da-164">Child Elements</span></span>  
 <span data-ttu-id="de1da-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="de1da-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de1da-166">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de1da-166">Parent Elements</span></span>  
  
|<span data-ttu-id="de1da-167">Élément</span><span class="sxs-lookup"><span data-stu-id="de1da-167">Element</span></span>|<span data-ttu-id="de1da-168">Description</span><span class="sxs-lookup"><span data-stu-id="de1da-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de1da-169">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="de1da-169">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="de1da-170">Définit les fonctionnalités de sécurité pour le [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="de1da-170">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de1da-171">Exemples</span><span class="sxs-lookup"><span data-stu-id="de1da-171">Example</span></span>  
 <span data-ttu-id="de1da-172">L'exemple suivant montre l'utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="de1da-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="de1da-173">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="de1da-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="de1da-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de1da-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="de1da-175">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="de1da-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="de1da-176">Liaisons</span><span class="sxs-lookup"><span data-stu-id="de1da-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="de1da-177">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="de1da-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="de1da-178">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="de1da-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="de1da-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="de1da-179">\<binding></span></span>](../../../misc/binding.md)
