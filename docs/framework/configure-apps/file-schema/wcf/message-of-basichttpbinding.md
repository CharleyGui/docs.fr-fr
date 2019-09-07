---
title: <message> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: bce80d96b1bcec0d580f2de3fe88d5fd6ad0a3b5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400262"
---
# <a name="message-of-basichttpbinding"></a>\<> de message \<de BasicHttpBinding >
Définit les paramètres pour la sécurité au niveau du message de l' [ \<> BasicHttpBinding](basichttpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> basicHttpBinding**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de messages**  
  
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
|algorithmSuite|Définit les algorithmes de chiffrement de message et de clé de type WRAP. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé. Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> La valeur par défaut est `Basic256`.|  
|clientCredentialType|Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages. Par défaut, il s’agit de `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|UserName|-Exige que le client soit authentifié auprès du serveur avec des informations d’identification de nom d’utilisateur. Ces informations d’identification doivent être spécifiées à l’aide de l' [ \<> ClientCredentials](clientcredentials.md).<br />-WCF ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide de mots de passe et l’utilisation de ces clés pour la sécurité de message. Par conséquent, WCF s’assure que le transport est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur. Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.|  
|Certificat|Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat. Dans ce cas, les informations d’identification du client doivent être spécifiées à l’aide [ \<de ClientCredentials >](clientcredentials.md) et du [ \<ClientCertificate >](clientcertificate-of-servicecredentials.md). De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service. Dans ce cas, les informations d’identification du service doivent <xref:System.ServiceModel.Description.ClientCredentials> être spécifiées à l’aide de l’élément Class ou `ClientCredentials` Behavior et le certificat de service est spécifié à l’aide de l' [ \<> serviceCertificate](servicecertificate-of-servicecredentials.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<> de sécurité](security-of-basichttpbinding.md)|Définit les fonctionnalités de sécurité pour le [ \<> BasicHttpBinding](basichttpbinding.md).|  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
