---
title: <message> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738960"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="adb05-102">\<message> de \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="adb05-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="adb05-103">Définit les paramètres pour la sécurité au niveau du message de [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="adb05-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="adb05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adb05-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adb05-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="adb05-105">Attributes and Elements</span></span>  
 <span data-ttu-id="adb05-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="adb05-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adb05-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="adb05-107">Attributes</span></span>  
  
|<span data-ttu-id="adb05-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="adb05-108">Attribute</span></span>|<span data-ttu-id="adb05-109">Description</span><span class="sxs-lookup"><span data-stu-id="adb05-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adb05-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="adb05-110">algorithmSuite</span></span>|<span data-ttu-id="adb05-111">Définit les algorithmes de chiffrement de message et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="adb05-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="adb05-112">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé.</span><span class="sxs-lookup"><span data-stu-id="adb05-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="adb05-113">Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="adb05-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="adb05-114">La valeur par défaut est `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="adb05-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="adb05-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="adb05-115">clientCredentialType</span></span>|<span data-ttu-id="adb05-116">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages.</span><span class="sxs-lookup"><span data-stu-id="adb05-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="adb05-117">Par défaut, il s’agit de `UserName`.</span><span class="sxs-lookup"><span data-stu-id="adb05-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="adb05-118">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="adb05-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="adb05-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="adb05-119">Value</span></span>|<span data-ttu-id="adb05-120">Description</span><span class="sxs-lookup"><span data-stu-id="adb05-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adb05-121">UserName</span><span class="sxs-lookup"><span data-stu-id="adb05-121">UserName</span></span>|<span data-ttu-id="adb05-122">-Exige que le client soit authentifié auprès du serveur avec des informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adb05-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="adb05-123">Ces informations d’identification doivent être spécifiées à l’aide de l' `clientCredentials` élément <>.</span><span class="sxs-lookup"><span data-stu-id="adb05-123">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="adb05-124">-WCF ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide de mots de passe et l’utilisation de ces clés pour la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="adb05-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="adb05-125">Par conséquent, WCF s’assure que le transport est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adb05-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="adb05-126">Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.</span><span class="sxs-lookup"><span data-stu-id="adb05-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="adb05-127">Certificat</span><span class="sxs-lookup"><span data-stu-id="adb05-127">Certificate</span></span>|<span data-ttu-id="adb05-128">Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="adb05-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="adb05-129">Dans ce cas, les informations d’identification du client doivent être spécifiées à l’aide de <`clientCredentials`> et du `clientCertificate`> <.</span><span class="sxs-lookup"><span data-stu-id="adb05-129">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="adb05-130">De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service.</span><span class="sxs-lookup"><span data-stu-id="adb05-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="adb05-131">Dans ce cas, les informations d’identification du service doivent être spécifiées à l’aide de l' <xref:System.ServiceModel.Description.ClientCredentials> élément Class ou `ClientCredentials` Behavior et la spécification du certificat de service à l’aide \<serviceCertificate> de l’élément de ServiceCredentials.</span><span class="sxs-lookup"><span data-stu-id="adb05-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adb05-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="adb05-132">Child Elements</span></span>  
 <span data-ttu-id="adb05-133">Aucune</span><span class="sxs-lookup"><span data-stu-id="adb05-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adb05-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="adb05-134">Parent Elements</span></span>  
  
|<span data-ttu-id="adb05-135">Élément</span><span class="sxs-lookup"><span data-stu-id="adb05-135">Element</span></span>|<span data-ttu-id="adb05-136">Description</span><span class="sxs-lookup"><span data-stu-id="adb05-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adb05-137"><`security`Élément> de <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="adb05-137"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="adb05-138">Définit les fonctionnalités de sécurité pour l' `netHttpBinding` élément <>.</span><span class="sxs-lookup"><span data-stu-id="adb05-138">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="adb05-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="adb05-139">Example</span></span>  
 <span data-ttu-id="adb05-140">Cet exemple montre comment implémenter une application qui utilise le basicHttpBinding et la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="adb05-140">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="adb05-141">Dans l'exemple de configuration suivant pour un service, la définition du point de terminaison spécifie le basicHttpBinding et référence une configuration de liaison nommée `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="adb05-141">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="adb05-142">Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section `behaviors` du fichier de configuration sous l'élément `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="adb05-142">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="adb05-143">Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section `behaviors` sous l'élément `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="adb05-143">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="adb05-144">Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.</span><span class="sxs-lookup"><span data-stu-id="adb05-144">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adb05-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb05-145">See also</span></span>

- [<span data-ttu-id="adb05-146">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="adb05-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="adb05-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="adb05-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="adb05-148">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="adb05-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="adb05-149">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="adb05-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
