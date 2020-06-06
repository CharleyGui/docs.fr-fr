---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: b3187cb51b6fd32797c9ad401c704d5f16c6f7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399910"
---
# \<secureConversationBootstrap>
Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationBootstrap>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
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
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|facultatif. Valeur booléenne qui spécifie si un jeton sérialisé peut être utilisé sur la réponse. La valeur par défaut est `false`. Si vous utilisez une liaison double, le paramètre a la valeur par défaut `true` et tout paramètre défini sera ignoré.|  
|`authenticationMode`|Spécifie le mode d'authentification SOAP utilisé entre l'initiateur et le répondeur.<br /><br /> La valeur par défaut est sspiNegotiated.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|La suite d'algorithmes de sécurité définit divers algorithmes, comme les algorithmes Canonicalization, Digest, KeyWrap, Signature, Encryption et KeyDerivation. Chacune de ces suites algorithmiques de sécurité définit des valeurs pour ces différents paramètres. La sécurité basée sur les messages est obtenue grâce à ces algorithmes.<br /><br /> Cet attribut est employé lors de l'utilisation d'une plate-forme différente qui opte pour un jeu d'algorithmes différent de la valeur par défaut. Vous devez connaître les forces et les faiblesses des algorithmes concernés lorsque vous modifiez ce paramètre. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Par défaut, il s’agit de `Basic256`.|  
|`includeTimestamp`|Valeur booléenne qui spécifie si les horodatages sont inclus dans chaque message. Par défaut, il s’agit de `true`.|  
|`keyEntropyMode`|Spécifie la manière dont les clés de sécurisation des messages sont calculées. Les clés peuvent être basées uniquement sur la clé du client, sur la clé du service ou sur une combinaison des deux. Les valeurs autorisées sont :<br /><br /> -ClientEntropy : la clé de session est basée sur le matériel de clé fourni par le client.<br />-ServerEntropy : la clé de session est basée sur le matériel de clé fourni par le service.<br />-CombinedEntropy : la clé de session est basée sur le support de clé fourni par le client et le service.<br /><br /> La valeur par défaut est CombinedEntropy.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Définit l'ordre dans lequel les algorithmes de sécurité au niveau du message sont appliqués au message. Les valeurs valides sont les suivantes :<br /><br /> -SignBeforeEncrypt : Connectez tout d’abord, puis chiffrez.<br />-SignBeforeEncryptAndEncryptSignature : signer, chiffrer et chiffrer la signature.<br />-EncryptBeforeSign : chiffre en premier, puis signe.<br /><br /> SignBeforeEncryptAndEncryptSignature est la valeur par défaut lors de l'utilisation de certificats mutuels avec WS-Security 1.1.  SignBeforeEncrypt est la valeur par défaut avec WS-Security 1.0.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Définit la version de WS-Security utilisée. Les valeurs valides sont les suivantes :<br /><br /> - WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> La valeur par défaut est WSSecurityXXX2005. Cet attribut est de type <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Valeur booléenne qui spécifie si les clés peuvent être dérivées des clés de vérification d'origine. Par défaut, il s’agit de `true`.|  
|`requireSecurityContextCancellation`|Valeur booléenne qui spécifie si le contexte de sécurité doit être annulé et arrêté lorsqu'il n'est plus requis. Par défaut, il s’agit de `true`.|  
|`requireSignatureConfirmation`|Valeur booléenne qui spécifie si la confirmation de signature WS-Security est activée. En cas de définition à `true`, les signatures de message sont confirmées par le répondeur. Par défaut, il s’agit de `false`.<br /><br /> La confirmation de signature est utilisée pour confirmer que le service répond en toute confiance à une demande.|  
|`securityHeaderLayout`|Spécifie le classement des éléments dans l'en-tête de sécurité. Les valeurs autorisées sont :<br /><br /> Interdire. Les éléments sont ajoutés à l’en-tête de sécurité conformément au principe général « déclarer avant d’utiliser ».<br />Strict. Les éléments sont ajoutés à l'en-tête de sécurité dans n'importe quel ordre qui confirme WSS: SOAP Message security.<br />- LaxWithTimestampFirst. Les éléments sont ajoutés à l'en-tête de sécurité dans n'importe quel ordre qui confirme WSS: SOAP Message security mais le premier élément dans l'en-tête de sécurité doit être un élément wsse:Timestamp.<br />- LaxWithTimestampLast. Les éléments sont ajoutés à l'en-tête de sécurité dans n'importe quel ordre qui confirme WSS: SOAP Message security mais le dernier élément dans l'en-tête de sécurité doit être un élément wsse:Timestamp.<br /><br /> La valeur par défaut est Strict.<br /><br /> Cet élément est de type <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Spécifie un jeton émis en cours. Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Spécifie les paramètres de sécurité d’un client local pour cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Spécifie les paramètres de sécurité d’un service local pour cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Spécifie les options de sécurité d’une liaison personnalisée.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Custom Binding Security](../../../wcf/samples/custom-binding-security.md)
