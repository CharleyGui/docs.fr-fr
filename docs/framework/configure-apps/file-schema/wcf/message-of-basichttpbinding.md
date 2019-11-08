---
title: <message> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 748a734af8cf6767ce47cfffce9aec3ef627cb44
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736740"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="e9580-102">\<> de message de \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e9580-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="e9580-103">Définit les paramètres pour la sécurité au niveau du message de la [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e9580-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="e9580-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9580-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9580-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e9580-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9580-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="e9580-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="e9580-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e9580-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="e9580-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="e9580-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="e9580-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-basichttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e9580-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="e9580-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="e9580-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9580-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9580-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9580-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e9580-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e9580-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e9580-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9580-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="e9580-114">Attributes</span></span>  
  
|<span data-ttu-id="e9580-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="e9580-115">Attribute</span></span>|<span data-ttu-id="e9580-116">Description</span><span class="sxs-lookup"><span data-stu-id="e9580-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9580-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e9580-117">algorithmSuite</span></span>|<span data-ttu-id="e9580-118">Définit les algorithmes de chiffrement de message et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="e9580-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e9580-119">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé.</span><span class="sxs-lookup"><span data-stu-id="e9580-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="e9580-120">Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="e9580-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="e9580-121">La valeur par défaut est `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="e9580-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="e9580-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e9580-122">clientCredentialType</span></span>|<span data-ttu-id="e9580-123">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages.</span><span class="sxs-lookup"><span data-stu-id="e9580-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="e9580-124">La valeur par défaut est `UserName`,</span><span class="sxs-lookup"><span data-stu-id="e9580-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e9580-125">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e9580-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e9580-126">valeur</span><span class="sxs-lookup"><span data-stu-id="e9580-126">Value</span></span>|<span data-ttu-id="e9580-127">Description</span><span class="sxs-lookup"><span data-stu-id="e9580-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9580-128">UserName</span><span class="sxs-lookup"><span data-stu-id="e9580-128">UserName</span></span>|<span data-ttu-id="e9580-129">-Exige que le client soit authentifié auprès du serveur avec des informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9580-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="e9580-130">Ces informations d’identification doivent être spécifiées à l’aide de la [\<ClientCredentials](clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e9580-130">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="e9580-131">-WCF ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide de mots de passe et l’utilisation de ces clés pour la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="e9580-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="e9580-132">Par conséquent, WCF s’assure que le transport est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9580-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="e9580-133">Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.</span><span class="sxs-lookup"><span data-stu-id="e9580-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="e9580-134">Certificat</span><span class="sxs-lookup"><span data-stu-id="e9580-134">Certificate</span></span>|<span data-ttu-id="e9580-135">Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="e9580-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="e9580-136">Les informations d’identification du client dans ce cas doivent être spécifiées à l’aide de [\<clientCredentials >](clientcredentials.md) et du [\<ClientCertificate](clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e9580-136">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="e9580-137">De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service.</span><span class="sxs-lookup"><span data-stu-id="e9580-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="e9580-138">Dans ce cas, les informations d’identification du service doivent être spécifiées à l’aide de <xref:System.ServiceModel.Description.ClientCredentials> classe ou `ClientCredentials` élément de comportement et en spécifiant le certificat de service à l’aide de la [\<serviceCertificate](servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e9580-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9580-139">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9580-139">Child Elements</span></span>  
 <span data-ttu-id="e9580-140">aucune.</span><span class="sxs-lookup"><span data-stu-id="e9580-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9580-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9580-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e9580-142">Élément</span><span class="sxs-lookup"><span data-stu-id="e9580-142">Element</span></span>|<span data-ttu-id="e9580-143">Description</span><span class="sxs-lookup"><span data-stu-id="e9580-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9580-144">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="e9580-144">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="e9580-145">Définit les fonctionnalités de sécurité pour le [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e9580-145">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9580-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="e9580-146">Example</span></span>  
 <span data-ttu-id="e9580-147">Cet exemple montre comment implémenter une application qui utilise le basicHttpBinding et la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="e9580-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="e9580-148">Dans l'exemple de configuration suivant pour un service, la définition du point de terminaison spécifie le basicHttpBinding et référence une configuration de liaison nommée `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="e9580-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="e9580-149">Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section `behaviors` du fichier de configuration sous l'élément `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="e9580-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="e9580-150">Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section `behaviors` sous l'élément `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="e9580-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="e9580-151">Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.</span><span class="sxs-lookup"><span data-stu-id="e9580-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
    <!-- This configuration defines the SecurityMode as Message and
         the clientCredentialType as Certificate. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
               is in the user's Trusted People store, then it will be trusted without performing a
               validation of the certificate's issuer chain. This setting is used here for convenience so that the
               sample can be run without having to have certificates issued by a certification authority (CA).
               This setting is less secure than the default, ChainTrust. The security implications of this
               setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9580-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9580-152">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="e9580-153">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e9580-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9580-154">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e9580-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9580-155">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e9580-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9580-156">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e9580-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e9580-157">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="e9580-157">\<binding></span></span>](bindings.md)
