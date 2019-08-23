---
title: <message> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 4a7606c0ebc9fc1bbd34aef619dcb4b8a1d63fa5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931544"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="a24f3-102">\<> de message \<de NetHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a24f3-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="a24f3-103">Définit les paramètres pour la sécurité au niveau du message de l' [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a24f3-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="a24f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a24f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a24f3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a24f3-105">\<bindings></span></span>  
<span data-ttu-id="a24f3-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a24f3-106">\<netHttpBinding></span></span>  
<span data-ttu-id="a24f3-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="a24f3-107">\<binding></span></span>  
<span data-ttu-id="a24f3-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="a24f3-108">\<security></span></span>  
<span data-ttu-id="a24f3-109">\<message></span><span class="sxs-lookup"><span data-stu-id="a24f3-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a24f3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a24f3-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a24f3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a24f3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a24f3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a24f3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a24f3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a24f3-113">Attributes</span></span>  
  
|<span data-ttu-id="a24f3-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a24f3-114">Attribute</span></span>|<span data-ttu-id="a24f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="a24f3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a24f3-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="a24f3-116">algorithmSuite</span></span>|<span data-ttu-id="a24f3-117">Définit les algorithmes de chiffrement de message et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="a24f3-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="a24f3-118">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé.</span><span class="sxs-lookup"><span data-stu-id="a24f3-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="a24f3-119">Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="a24f3-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="a24f3-120">La valeur par défaut est `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="a24f3-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="a24f3-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a24f3-121">clientCredentialType</span></span>|<span data-ttu-id="a24f3-122">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages.</span><span class="sxs-lookup"><span data-stu-id="a24f3-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="a24f3-123">Par défaut, il s’agit de `UserName`.</span><span class="sxs-lookup"><span data-stu-id="a24f3-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a24f3-124">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a24f3-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a24f3-125">Valeur</span><span class="sxs-lookup"><span data-stu-id="a24f3-125">Value</span></span>|<span data-ttu-id="a24f3-126">Description</span><span class="sxs-lookup"><span data-stu-id="a24f3-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a24f3-127">UserName</span><span class="sxs-lookup"><span data-stu-id="a24f3-127">UserName</span></span>|<span data-ttu-id="a24f3-128">-Exige que le client soit authentifié auprès du serveur avec des informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a24f3-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="a24f3-129">Ces informations d’identification doivent être spécifiées à`clientCredentials`l’aide de l’élément < >.</span><span class="sxs-lookup"><span data-stu-id="a24f3-129">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="a24f3-130">-WCF ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide de mots de passe et l’utilisation de ces clés pour la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="a24f3-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="a24f3-131">Par conséquent, WCF s’assure que le transport est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a24f3-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="a24f3-132">Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.</span><span class="sxs-lookup"><span data-stu-id="a24f3-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="a24f3-133">Certificat</span><span class="sxs-lookup"><span data-stu-id="a24f3-133">Certificate</span></span>|<span data-ttu-id="a24f3-134">Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="a24f3-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="a24f3-135">Dans ce cas, les informations d’identification du client doivent être`clientCredentials`spécifiées à l'`clientCertificate`aide de < > et du > <.</span><span class="sxs-lookup"><span data-stu-id="a24f3-135">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="a24f3-136">De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service.</span><span class="sxs-lookup"><span data-stu-id="a24f3-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="a24f3-137">Dans ce cas, les informations d’identification du service doivent <xref:System.ServiceModel.Description.ClientCredentials> être spécifiées à l’aide de l’élément Class ou \< `ClientCredentials` Behavior et la spécification du certificat de service à l’aide de l’élément serviceCertificate > de ServiceCredentials.</span><span class="sxs-lookup"><span data-stu-id="a24f3-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a24f3-138">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a24f3-138">Child Elements</span></span>  
 <span data-ttu-id="a24f3-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="a24f3-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a24f3-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a24f3-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a24f3-141">Élément</span><span class="sxs-lookup"><span data-stu-id="a24f3-141">Element</span></span>|<span data-ttu-id="a24f3-142">Description</span><span class="sxs-lookup"><span data-stu-id="a24f3-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a24f3-143"><`security`élément > de <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="a24f3-143"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="a24f3-144">Définit les fonctionnalités de sécurité pour l'`netHttpBinding`élément < >.</span><span class="sxs-lookup"><span data-stu-id="a24f3-144">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a24f3-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="a24f3-145">Example</span></span>  
 <span data-ttu-id="a24f3-146">Cet exemple montre comment implémenter une application qui utilise le basicHttpBinding et la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="a24f3-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="a24f3-147">Dans l'exemple de configuration suivant pour un service, la définition du point de terminaison spécifie le basicHttpBinding et référence une configuration de liaison nommée `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="a24f3-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="a24f3-148">Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section `behaviors` du fichier de configuration sous l'élément `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="a24f3-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="a24f3-149">Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section `behaviors` sous l'élément `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="a24f3-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="a24f3-150">Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.</span><span class="sxs-lookup"><span data-stu-id="a24f3-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
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
      <binding name="Binding1" >
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
  
## <a name="see-also"></a><span data-ttu-id="a24f3-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a24f3-151">See also</span></span>

- [<span data-ttu-id="a24f3-152">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a24f3-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a24f3-153">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a24f3-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a24f3-154">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a24f3-154">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a24f3-155">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a24f3-155">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a24f3-156">\<binding></span><span class="sxs-lookup"><span data-stu-id="a24f3-156">\<binding></span></span>](../../../misc/binding.md)
