---
title: <security> de <customBinding>
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: 454113f66007ddd69f8455bb532e9cbd12fcefb7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738698"
---
# <a name="security-of-custombinding"></a>\<security> de \<customBinding>
Spécifie les options de sécurité d’une liaison personnalisée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
          authenticationMode="AuthenticationMode"
          defaultAlgorithmSuite="SecurityAlgorithmSuite"
          includeTimestamp="Boolean"
          requireDerivedKeys="Boolean"
          keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
          messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
          messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
          requireDerivedKeys="Boolean"
          requireSecurityContextCancellation="Boolean"
          requireSignatureConfirmation="Boolean"
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|facultatif. Valeur booléenne qui spécifie si un jeton sérialisé peut être utilisé sur la réponse. La valeur par défaut est `false`. Si vous utilisez une liaison double, le paramètre a la valeur par défaut `true` et tout paramètre défini sera ignoré.|  
|authenticationMode|facultatif. Spécifie le mode d'authentification utilisé entre l'initiateur et le répondeur. Reportez-vous ci-dessous pour connaître toutes les valeurs.<br /><br /> Par défaut, il s’agit de `sspiNegotiated`.|  
|defaultAlgorithmSuite|facultatif. Définit les algorithmes de chiffrement de message et de clé de type WRAP. Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Les valeurs possibles sont indiquées ci-dessous. La valeur par défaut est `Basic256`.<br /><br /> Cet attribut est employé lors de l'utilisation d'une plate-forme différente qui opte pour un jeu d'algorithmes différent de la valeur par défaut. Vous devez connaître les forces et les faiblesses des algorithmes concernés lorsque vous modifiez ce paramètre. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Valeur booléenne qui spécifie si les horodatages sont inclus dans chaque message. Par défaut, il s’agit de `true`.|  
|keyEntropyMode|Spécifie la manière dont les clés de sécurisation des messages sont calculées. Les clés peuvent être basées uniquement sur la clé du client, sur la clé du service ou sur une combinaison des deux. Les valeurs valides sont les suivantes :<br /><br /> -   `ClientEntropy`: La clé de session est basée sur les données de clé fournies par le client.<br />-   `ServerEntropy`: La clé de session est basée sur les données de clés fournies par le serveur.<br />-   `CombinedEntropy`: La clé de session est basée sur les données de clé fournies par le client et le service.<br /><br /> Par défaut, il s’agit de `CombinedEntropy`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Définit l'ordre dans lequel les algorithmes de sécurité au niveau du message sont appliqués au message. Les valeurs valides sont les suivantes :<br /><br /> -   `SignBeforeEncrypt`: Signer en premier, puis chiffrer.<br />-   `SignBeforeEncryptAndEncryptSignature`: Signer en premier, chiffrer, puis chiffrer la signature.<br />-   `EncryptBeforeSign`: Chiffrer en premier, puis signer.<br /><br /> La valeur par défaut dépend de la version de WS-Security qui est utilisée. La valeur par défaut est `SignBeforeEncryptAndEncryptSignature` lors de l'utilisation de WS-Security 1,1. La valeur par défaut est `SignBeforeEncrypt` lors de l'utilisation de WS-Security 1.0.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|facultatif. Définit la version de WS-Security utilisée. Les valeurs valides sont les suivantes :<br /><br /> - WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />- WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />- WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> La valeur par défaut est WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 et peut être simplement exprimée en XML par `Default`. Cet attribut est de type <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Valeur booléenne qui spécifie si les clés peuvent être dérivées des clés de vérification d'origine. Par défaut, il s’agit de `true`.|  
|requireSecurityContextCancellation|facultatif. Valeur booléenne qui spécifie si le contexte de sécurité doit être annulé et arrêté lorsqu'il n'est plus exigé. Par défaut, il s’agit de `true`.|  
|requireSignatureConfirmation|facultatif. Valeur booléenne qui spécifie si la confirmation de signature WS-Security est activée. En cas de définition à `true`, les signatures de message sont confirmées par le répondeur.  Lorsque la liaison personnalisée est configurée pour des certificats mutuels ou si elle est configurée pour utiliser des jetons émis (liaisons WSS 1.1) cet attribut a la valeur par défaut `true`. Sinon, la valeur par défaut est `false`.<br /><br /> La confirmation de signature est utilisée pour confirmer que le service répond en toute confiance à une demande.|  
|securityHeaderLayout|facultatif. Spécifie le classement des éléments dans l'en-tête de sécurité. Les valeurs valides sont les suivantes :<br /><br /> -   `Strict`: Les éléments sont ajoutés à l’en-tête de sécurité conformément au principe général de « déclarer avant d’utiliser ».<br />-   `Lax`: Les éléments sont ajoutés à l’en-tête de sécurité dans n’importe quel ordre qui confirme la sécurité des messages WSS : SOAP.<br />-   `LaxWithTimestampFirst`: Les éléments sont ajoutés à l’en-tête de sécurité dans n’importe quel ordre qui confirme la sécurité des messages WSS : SOAP, sauf que le premier élément de l’en-tête de sécurité doit être un élément wsse : timestamp.<br />-   `LaxWithTimestampLast`: Les éléments sont ajoutés à l’en-tête de sécurité dans n’importe quel ordre qui confirme la sécurité des messages WSS : SOAP, sauf que le dernier élément de l’en-tête de sécurité doit être un élément wsse : timestamp.<br /><br /> Par défaut, il s’agit de `Strict`.<br /><br /> Cet élément est de type <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Basic128|Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192|Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256|Utilisez le chiffrement Aes256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|TripleDes|Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesRsa15|Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|Basic128Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192Sha256|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|TripleDesSha256|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Sha256Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Sha256Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|Basic256Sha256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesSha256Rsa15|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Spécifie un jeton émis en cours. Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Spécifie les paramètres de sécurité d’un client local pour cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Spécifie les paramètres de sécurité d’un service local pour cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur l’utilisation de cet élément, consultez [modes d’authentification SecurityBindingElement](../../../wcf/feature-details/securitybindingelement-authentication-modes.md) et [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer la sécurité à l’aide d’une liaison personnalisée. Il indique également comment utiliser une liaison personnalisée afin d’activer la sécurité de niveau message à l’aide d’un transport sécurisé. Cette configuration est utile lorsqu'un transport sécurisé est requis pour la transmission des messages entre le client et le service et que ces messages doivent en même temps bénéficier d'une sécurité de niveau message. Cette configuration n’est pas prise en charge par les liaisons fournies par le système.  
  
 La configuration du service définit une liaison personnalisée qui prend en charge la communication TCP protégée à l'aide du protocole TLS/SSL et de la sécurité des messages Windows. La liaison personnalisée utilise un certificat de service afin d’authentifier le service au niveau du transport et de protéger les messages pendant leur transmission entre le client et le service. Cela est accompli par l' [\<sslStreamSecurity>](sslstreamsecurity.md) élément de liaison. Le certificat du service est configuré à l'aide d'un comportement de service.  
  
 En outre, la liaison personnalisée utilise la sécurité de niveau message avec le type d’informations d’identification Windows, c’est-à-dire le type par défaut. Cela est accompli par l’élément de liaison de [sécurité](security-of-custombinding.md) . Le client et le service sont tous deux authentifiés à l'aide de la sécurité de niveau message lorsque le mécanisme d'authentification Kerberos est disponible. Si le mécanisme d'authentification Kerberos n'est pas disponible, l'authentification NTLM est utilisée. NTLM authentifie le client auprès du service mais n'authentifie pas le service auprès du client. L’élément de liaison de [sécurité](security-of-custombinding.md) est configuré pour utiliser `SecureConversation` AuthenticationType, ce qui entraîne la création d’une session de sécurité sur le client et le service. Ceci est nécessaire pour permettre au contrat duplex du service de fonctionner. Pour plus d’informations sur l’exécution de cet exemple, consultez sécurité de la [liaison personnalisée](../../../wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- use following base address -->
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>
          </baseAddresses>
        </host>
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <!-- configure a custom binding -->
      <customBinding>
        <binding name="Binding1">
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
          <serviceCredentials>
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Custom Binding Security](../../../wcf/samples/custom-binding-security.md)
