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
# <a name="message-of-nethttpbinding"></a>\<message> de \<netHttpBinding>
Définit les paramètres pour la sécurité au niveau du message de [\<netHttpBinding>](nethttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|algorithmSuite|Définit les algorithmes de chiffrement de message et de clé de type WRAP. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> La valeur par défaut est `Basic256`.|  
|clientCredentialType|Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages. Par défaut, il s’agit de `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|UserName|-Exige que le client soit authentifié auprès du serveur avec des informations d’identification de nom d’utilisateur. Ces informations d’identification doivent être spécifiées à l’aide de l' `clientCredentials` élément <>.<br />-WCF ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide de mots de passe et l’utilisation de ces clés pour la sécurité de message. Par conséquent, WCF s’assure que le transport est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur. Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.|  
|Certificat|Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat. Dans ce cas, les informations d’identification du client doivent être spécifiées à l’aide de <`clientCredentials`> et du `clientCertificate`> <. De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service. Dans ce cas, les informations d’identification du service doivent être spécifiées à l’aide de l' <xref:System.ServiceModel.Description.ClientCredentials> élément Class ou `ClientCredentials` Behavior et la spécification du certificat de service à l’aide \<serviceCertificate> de l’élément de ServiceCredentials.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|<`security`Élément> de <`netHttpBinding`>|Définit les fonctionnalités de sécurité pour l' `netHttpBinding` élément <>.|  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment implémenter une application qui utilise le basicHttpBinding et la sécurité de message. Dans l'exemple de configuration suivant pour un service, la définition du point de terminaison spécifie le basicHttpBinding et référence une configuration de liaison nommée `Binding1`. Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section `behaviors` du fichier de configuration sous l'élément `serviceCredentials`. Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section `behaviors` sous l'élément `clientCertificate`.  
  
 Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
