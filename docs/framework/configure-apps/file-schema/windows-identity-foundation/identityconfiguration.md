---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251994"
---
# \<identityConfiguration>

Spécifie les paramètres d’identité au niveau du service.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a>Syntaxe

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Nom de la section de configuration de l’identité. Vous pouvez utiliser ce nom pour faire référence à une section de configuration spécifique. Si aucun `name` attribut n’est spécifié, la section définit la configuration par défaut. La configuration par défaut est toujours utilisée pour les scénarios de fédération passive. Pour plus d’informations, consultez l' [\<federationConfiguration>](federationconfiguration.md) élément.|
|saveBootstrapContext|Spécifie si les jetons de démarrage doivent être inclus dans le jeton de session. La valeur peut également être définie sur une collection de gestionnaires de jetons en définissant l' `saveBootstrapContext` attribut sur l' [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|
|maximumClockSkew|<xref:System.TimeSpan>Qui spécifie la variation d’horloge maximale autorisée. Contrôle la variation d’horloge maximale autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation du délai d’expiration d’une session de connexion. La valeur par défaut est 5 minutes, « 00:05:00 ». Pour plus d’informations sur la spécification des <xref:System.TimeSpan> valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md). La décalage d’horloge maximal peut également être défini sur une collection de gestionnaires de jetons en définissant l' `maximumClockSkew` attribut sur l' [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<caches>](caches.md)|Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. facultatif.|
|[\<certificateValidation>](certificatevalidation.md)|Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. facultatif.|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes. facultatif.|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|Inscrit un gestionnaire d’autorisations des revendications pour les revendications entrantes. facultatif.|
|[\<claimTypeRequired>](claimtyperequired.md)|Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants. facultatif.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité. Zéro, une ou plusieurs collections de gestionnaires de jetons de sécurité peuvent être spécifiées. facultatif.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Fournit la configuration permettant d’activer les options de Windows Identity Foundation (WIF) dans les applications.|

## <a name="remarks"></a>Remarques

Plusieurs configurations d’identité peuvent être définies, chacune avec un nom unique. Le comportement est le suivant :

1. Si aucun `<identityConfiguration>` élément n’est spécifié. Une configuration d’identité par défaut est créée au moment de l’exécution et remplie avec les valeurs par défaut.

2. Si un seul `<identityConfiguration>` élément est spécifié. Il s’agit de la configuration d’identité par défaut. Peu importe s’il est nommé ou sans nom.

3. Si plusieurs `<identityConfiguration>` éléments sont spécifiés. L’élément sans nom spécifie la configuration d’identité par défaut. Lorsque vous spécifiez plusieurs éléments, il est recommandé `<identityConfiguration>` de ne pas nommer l’un d’eux.

> [!WARNING]
> Si vous spécifiez plusieurs `<identityConfiguration>` éléments, l’un d’eux doit être sans nom. L’élément sans nom est la configuration d’identité par défaut.

 Certains des paramètres spécifiés dans l' `<identityConfiguration>` élément peuvent être remplacés par des paramètres sur une collection de gestionnaires de jetons de sécurité ou par des paramètres sur des gestionnaires de jetons de sécurité individuels.

> [!IMPORTANT]
> Lors de l’utilisation de la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité référencée par l' `<federationConfiguration>` élément configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour prendre des décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs, par exemple des applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, l' [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée sont les seuls paramètres appliqués. Tous les autres paramètres sont ignorés. Pour plus d’informations, consultez l' [\<federationConfiguration>](federationconfiguration.md) élément.

L' `<identityConfiguration>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> classe. Une section de configuration d’identité est représentée par la <xref:System.IdentityModel.Configuration.IdentityConfiguration> classe.

> [!IMPORTANT]
> La spécification des éléments suivants en tant qu’éléments enfants de l' `<identityConfiguration>` élément a été dépréciée, bien que le comportement soit toujours pris en charge pour la compatibilité descendante. Ces éléments doivent plutôt être spécifiés sous l' [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) élément.
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a>Exemple

L’exemple suivant crée une configuration d’identité nommée « alternateConfiguration ». La configuration d’identité spécifie les paramètres par défaut.

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
