---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732738"
---
# <a name="transport-of-wshttpbinding"></a>\<transport> de \<wsHttpBinding>

Définit les paramètres d'authentification correspondant au transport HTTP.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a>Syntaxe

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>Type

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`clientCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service. Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.|
|`proxyCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine. Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.|
|`realm`|Chaîne indiquant le domaine de l’authentification de base ou Digest. La valeur par défaut est une chaîne vide.<br /><br /> Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification. Il peut également spécifier une collection d’utilisateurs disposant d’un accès. Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.|
|`policyEnforcement`|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).<br />2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3. Always : la stratégie est toujours appliquée. Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|

## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType

|Valeur|Description|
|-----------|-----------------|
|`None`|La sécurité est désactivée.|
|`Basic`|Utilise l'authentification de base.|
|`Digest`|Utilise l’authentification Digest.|
|`Ntlm`|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|
|`Windows`|Utilise l'authentification intégrée Windows.|
|`Certificate`|Utilise des certificats X.509 pour authentifier le client.|

## <a name="proxycredentialtype-attribute"></a>Attribut proxyCredentialType

|Valeur|Description|
|-----------|-----------------|
|`None`|La sécurité est désactivée.|
|`Basic`|Utilise l'authentification de base.|
|`Digest`|Utilise l’authentification Digest.|
|`Ntlm`|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|
|`Windows`|Utilise l'authentification intégrée Windows.|
|`Certificate`|Utilise des certificats X.509 pour authentifier le client.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|Représente les fonctionnalités de sécurité de [\<wsHttpBinding>](wshttpbinding.md) .|

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
