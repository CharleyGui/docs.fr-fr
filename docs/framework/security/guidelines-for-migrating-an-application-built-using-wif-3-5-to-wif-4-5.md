---
title: Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: 645fd09de91d8190384faea9df2ef18511162c2f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834523"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5

## <a name="applies-to"></a>S'applique à

- Microsoft® Windows® Identity Foundation (WIF) 3.5 et 4.5.

## <a name="overview"></a>Vue d'ensemble

WIF (Windows Identity Foundation) a été initialement mis en production au moment de .NET 3.5 SP1. Cette version de WIF est appelée WIF 3.5. Elle a été publiée sous la forme d’un runtime et d’un kit SDK distincts, ce qui signifiait que le runtime WIF devait être installé sur chaque ordinateur sur lequel une application WIF était exécutée et que les développeurs devaient télécharger et installer le kit SDK WIF pour obtenir les outils et les modèles Visual Studio qui permettaient le développement des applications WIF. À compter de .NET 4.5, WIF a été entièrement intégré dans le .NET Framework. Un runtime distinct n’est plus nécessaire et les outils WIF peuvent être installés dans Visual Studio 2012 à l’aide du Gestionnaire d’extensions Visual Studio. Cette version de WIF est appelée WIF 4.5.

L’intégration de WIF dans .NET a nécessité plusieurs modifications de la surface de l’API WIF. WIF 4.5 comprend de nouveaux espaces de noms, certaines modifications apportées aux éléments de configuration et de nouveaux outils pour Visual Studio. Cette rubrique fournit des conseils que vous pouvez utiliser pour vous aider à migrer les applications générées à l’aide de WIF 3.5 vers WIF 4.5. Il peut exister des scénarios dans lesquels vous devez exécuter des applications héritées générées à l’aide de WIF 3.5 sur des ordinateurs exécutant Windows 8 ou Windows Server 2012. Cette rubrique fournit également des conseils sur l’activation de WIF 3.5 pour ces systèmes d’exploitation.

## <a name="changes-required-for-wif-45"></a>Modifications requises pour WIF 4.5

Cette section décrit les modifications qui sont nécessaires pour migrer une application WIF 3.5 vers WIF 4.5.

### <a name="assembly-and-namespace-changes"></a>Modifications des assemblys et des espaces de noms

Dans WIF 3.5, toutes les classes WIF étaient contenues dans l’assembly `Microsoft.IdentityModel` (microsoft.identitymicrosoft.identitymodel.dll). Dans WIF 4.5, les classes WIF ont été réparties dans les assemblys suivants : `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) et `System.ServiceModel` (System.ServiceModel.dll).

Les classes WIF 3.5 étaient toutes contenues dans l’un des espaces de noms `Microsoft.IdentityModel`, par exemple `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`, et ainsi de suite. Dans WIF 4.5, les classes WIF sont désormais réparties sur les espaces de noms [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004), l’espace de noms <xref:System.Security.Claims?displayProperty=nameWithType> et l’espace de noms <xref:System.ServiceModel.Security?displayProperty=nameWithType>. En plus de cette réorganisation, certaines classes WIF 3.5 ont été abandonnées dans WIF 4.5.

Le tableau suivant répertorie certains des plus importants espaces de noms WIF 4.5 et le type des classes qu’ils contiennent. Pour plus d’informations sur le mappage des espaces de noms entre WIF 3.5 et WIF 4.5 ainsi que sur les espaces de noms et les classes qui ont été abandonnés dans WIF 4.5, consultez [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|Espace de noms WIF 4.5|Description|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Contient des classes qui représentent des transformations de cookies, des services d’émission de jeton de sécurité et des lecteurs de dictionnaires XML spécifiques. Contient des classes des espaces de noms WIF 3.5 suivants : `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService` et `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Contient des classes qui représentent des revendications, des identités basées sur les revendications, des principaux basés sur les revendications et d’autres artefacts de modèles d’identité basés sur les revendications. Contient des classes de l’espace de noms `Microsoft.IdentityModel.Claims`.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Contient des classes qui représentent des jetons de sécurité, des gestionnaires de jetons de sécurité et d’autres artefacts de jetons de sécurité. Contient des classes des espaces de noms WIF 3.5 suivants : `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11` et `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Contient des classes qui sont utilisées dans des scénarios passifs (WS-Federation). Contient des classes de l’espace de noms `Microsoft.IdentityModel.Web`.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Les classes qui représentent des contrats WCF, des canaux, des hôtes de service et d’autres artefacts utilisés dans des scénarios actifs (WS-Trust) figurent désormais dans cet espace de noms. Dans WIF 3.5, ces classes se trouvaient dans l’espace de noms `Microsoft.IdentityModel.Protocols.WSTrust`.|

> [!IMPORTANT]
> Les espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d’identité basé sur des revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> et <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Le modèle d'identité basé sur des revendications WCF est remplacé par WIF. Vous ne devez pas utiliser les classes de ces trois espaces de noms quand vous créez des solutions basées sur WIF.

### <a name="changes-due-to-net-integration"></a>Modifications en raison de l’intégration dans .NET

WIF est maintenant intégré dans le .NET Framework. La plupart des classes de principaux et d’identités .NET dérivent maintenant de <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> et <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Cela aboutit aux modifications suivantes dans WIF 4.5 :

- Les classes WIF qui représentent des revendications, des identités et des principaux existent maintenant dans l’espace de noms <xref:System.Security.Claims?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > L’espace de noms <xref:System.IdentityModel.Claims?displayProperty=nameWithType> contient des classes qui représentent des artefacts dans le modèle d’identité basé sur des revendications WCF. Un grand nombre de ces classes ont des noms identiques aux classes WIF, par exemple `Claims`. N’utilisez pas ces classes lors de la génération de solutions basées sur WIF.

- Les classes de principaux et d’identités .NET dérivent maintenant directement de <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> et <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, qui représentent des principaux et identités basés sur les revendications. Pour cette raison, les interfaces WIF 3.5 `IClaimsIdentity` et `IClaimsPrincipal` ne sont plus nécessaires et ne sont pas disponibles dans WIF 4.5.

- Comme les classes de principaux et d’identités .NET telles que <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> et <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> dérivent maintenant de <xref:System.Security.Claims.ClaimsIdentity> et <xref:System.Security.Claims.ClaimsPrincipal>, elles possèdent des fonctionnalités de revendications intégrées. Pour cette raison, les classes de principaux et d’identités spécifiques aux revendications telles que `WindowsClaimsIdentity` et `WindowsClaimsPrincipal` qui étaient présentes dans WIF 3.5 ne sont plus nécessaires et n’existent pas dans WIF 4.5.

### <a name="other-changes-to-wif-functionality"></a>Autres modifications apportées aux fonctionnalités WIF

Outre celles des espaces de noms et celles dues à l’intégration dans .NET, les modifications générales suivantes sont apportées aux fonctionnalités WIF dans WIF 4.5.

- La classe `Microsoft.IdentityModel.ExceptionMapper`, qui offrait des fonctionnalités vous permettant de mapper des exceptions à des erreurs SOAP spécifiques, est supprimée.

- La surface de l’exception a été considérablement réduite.

- Un grand nombre des classes qui définissaient des constantes spécifiques au protocole ou à WS-* ont été supprimées, par exemple la classe `Microsoft.IdentityModel.WSAddressing10Constants` qui définissait des constantes liées à WS-Addressing 1.0.

- Le service d’émission de jetons Revendications vers Windows (c2wts) et ses classes associées dans l’espace de noms `Microsoft.IdentityModel.WindowsTokenService` sont supprimés.

### <a name="wif-configuration-changes"></a>Modifications de configuration WIF

La plupart des modifications dans le fichier de configuration ont été provoquées par les mises à jour des espaces de noms dans WIF 4.5. Par exemple, considérez l’entrée WIF 3.5 suivante dans la section `<httpModules>` pour ajouter le gestionnaire d’authentification WS-Federation à une application :

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Cette entrée a été mise à jour dans WIF 4.5 pour inclure les nouveaux espaces de noms et la version de l’assembly :

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

La liste suivante répertorie les principales modifications apportées au fichier de configuration pour WIF 4.5.

- La section `<microsoft.identityModel>` est devenue la section [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md).

- L’élément `<service>` est devenu l’élément [\<identityConfiguration>](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).

- Une nouvelle section, [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), a été ajoutée pour spécifier les paramètres qui contrôlent le comportement dans les scénarios passifs (WS-Federation).

- L’élément [\<federationConfiguration>](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) et ses éléments enfants ont été déplacés de l’élément `<service>` dans WIF 3.5 vers le nouvel élément `<system.identityModel.services>`.

- Plusieurs éléments qui pouvaient être spécifiés au niveau service directement sous l’élément `<service>` dans WIF 3.5 ne peuvent plus être spécifiés que sous l’élément [\<securityTokenHandlerConfiguration>](../configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md). (Ils peuvent toujours être spécifiés sous l’élément [\<identityConfiguration>](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) dans WIF 4.5 pour la compatibilité descendante.)

Pour obtenir une liste complète des éléments de configuration WIF 4.5, consultez [Schéma de configuration de Windows Identity Foundation](../configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Modifications des outils Visual Studio

Le Kit SDK WIF 3.5 proposait un utilitaire de fédération autonome, FedUtil.exe (FedUtil), que vous pouviez utiliser pour externaliser la gestion des identités dans les applications WIF vers un service d’émission de jeton de sécurité (STS). Cet outil ajoutait des paramètres WIF au fichier de configuration de l’application pour permettre à l’application d’obtenir des jetons de sécurité à partir d’un ou de plusieurs services STS et a été exposé dans Visual Studio via le bouton **Add STS Service Reference** (Ajouter une référence de service STS). FedUtil n’est pas livré avec WIF 4.5. Au lieu de cela, WIF 4.5 prend en charge une nouvelle extension Visual Studio nommée Identity and Access Tool pour Visual Studio 2012 que vous pouvez utiliser pour modifier le fichier de configuration de votre application avec les paramètres WIF requis pour externaliser la gestion des identités vers un service STS. L’outil Identity and Access Tool implémente également un service STS appelé STS local que vous pouvez utiliser pour tester vos applications WIF. Dans de nombreux cas, cette fonctionnalité évite d’avoir à générer des services STS personnalisés qui étaient souvent nécessaires dans WIF 3.5 pour tester des solutions en cours de développement. Pour cette raison, les modèles STS ne sont plus pris en charge dans Visual Studio 2012 ; toutefois, les classes qui prennent en charge le développement de services STS sont toujours disponibles dans WIF 4.5.

Vous pouvez installer l’outil Identity and Access Tool à partir du gestionnaire des extensions et des mises à jour dans Visual Studio, ou vous pouvez le télécharger à partir de la page suivante de la Galerie de code : [Identity and Access Tool pour Visual Studio 2012 sur la Galerie de code](https://go.microsoft.com/fwlink/?LinkID=245849). Les modifications des outils Visual Studio sont résumées dans la liste suivante :

- La fonctionnalité Add STS Service Reference (Ajouter une référence de service STS) est supprimée. Elle est remplacée par l’outil Identity and Access Tool.

- Les modèles STS Visual Studio sont supprimés. Vous pouvez utiliser le service STS local qui est disponible via l’outil Identity and Access Tool pour tester des solutions relatives aux identités que vous développez avec WIF. La configuration du service STS local peut être modifiée pour personnaliser les revendications qu’il sert.

- L’utilitaire de fédération autonome (FedUtil) n’est pas disponible dans WIF 4.5. Vous pouvez utiliser l’outil Identity and Access Tool pour modifier vos fichiers de configuration afin d’externaliser la gestion des identités vers un service STS.

Pour plus d’informations sur l’outil Identity and Access Tool, consultez [Identity and Access Tool for Visual Studio 2012](identity-and-access-tool-for-vs.md).

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Scénarios passifs (WS-Federation) :

- Les classes qui prennent en charge les scénarios passifs ont été déplacées vers l’espace de noms <xref:System.IdentityModel.Services?displayProperty=nameWithType>. Dans WIF 3.5, ces classes se trouvaient dans l’espace de noms `Microsoft.IdentityModel.Web`.

- Les classes dans l’espace de noms `Microsoft.IdentityModel.Web.Configuration` ont été déplacées vers <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Ces classes représentent des objets spécifiques à la configuration dans les scénarios passifs.

- `FederatedPassiveSignInControl` n’est plus pris en charge ; toutes les classes dans l’espace de noms `Microsoft.IdentityModel.Web.Controls` ont été supprimées de WIF 4.5.

- La fonctionnalité de déconnexion du module d’authentification WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) est différente de celle dans WIF 3.5. Pour plus d’informations sur le fonctionnement de la déconnexion dans WIF 4.5, consultez la rubrique de la classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.

### <a name="active-wcfws-trust-scenarios"></a>Scénarios actifs (WCF/WS-Trust) :

- L’espace de noms `Microsoft.IdentityModel.Protocols.WSTrust` a été divisé principalement en deux espaces de noms dans WIF 4.5. Les classes qui représentent des artefacts spécifiques au protocole WS-Trust se trouvent maintenant dans <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Cela inclut les classes comme <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Les classes qui représentent des contrats de service, des canaux, des hôtes de service et d’autres artefacts qui interviennent dans l’utilisation de WS-Trust dans les applications WCF ont été déplacées vers <xref:System.ServiceModel.Security?displayProperty=nameWithType>, par exemple l’interface <xref:System.ServiceModel.Security.IWSTrust13AsyncContract>.

- La configuration d’une application WCF pour utiliser WIF a été considérablement simplifiée. Auparavant, l’élément `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` devait être ajouté comme une extension de comportement et cette fonctionnalité était alors utilisée pour insérer WIF dans le comportement de service en spécifiant un élément `<federatedServiceHostConfiguration>`. WIF 4.5 a été plus étroitement intégré dans WCF. Vous activez maintenant WIF sur un service WCF en spécifiant l’attribut `useIdentityConfiguration` sur l’élément `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` comme dans le XML suivant :

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- Dans WIF 4.5, le certificat de service utilisé par un service actif (WCF) doit être spécifié sur l’hôte de service. Dans la configuration, vous pouvez effectuer cette opération via l’élément `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>`/`<serviceCertificate>`, comme indiqué dans l’exemple précédent. Dans WIF 3.5, le certificat de service peut être spécifié par l’élément enfant `<serviceCertificate>` de l’élément WIF `<service>`. Cette fonctionnalité n’existe pas dans WIF 4.5 ; spécifiez l’élément `<serviceCertificate>` sous l’élément `<serviceCredentials>` à la place.

- Les classes utilisées pour insérer WIF 3.5 dans WCF n’existent plus. Cela inclut les classes suivantes dans l’espace de noms `Microsoft.IdentityModel.Tokens` : `FederatedSecurityTokenManager`, `FederatedServiceCredentials` et `IdentityModelServiceAuthorizationManager`, ainsi que la classe `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement`.

## <a name="enabling-wif-35-in-windows-8"></a>Activation de WIF 3.5 dans Windows 8

Comme WIF 4.5 fait partie de .NET 4.5, il est automatiquement activé sur les ordinateurs exécutant Windows 8 et Windows Server 2012, et les applications générées à l’aide de WIF 4.5 sont exécutées sous Windows 8 ou Windows Server 2012 par défaut. Toutefois, vous devrez peut-être exécuter des applications qui ont été générées à l’aide de WIF 3.5 sur un ordinateur qui exécute Windows 8 ou Windows Server 2012. Dans ce cas, vous devez activer WIF 3.5 sur l’ordinateur cible. Sur un ordinateur exécutant Windows 8, vous pouvez effectuer cette opération à l’aide de l’outil Gestion et maintenance des images de déploiement (DISM). Sur un ordinateur exécutant Windows Server 2012, vous pouvez utiliser l’outil DISM ou l’applet de commande Windows PowerShell `Add-WindowsFeature`. Dans les deux cas, les commandes appropriées peuvent être appelées à partir de la ligne de commande ou de l’environnement Windows PowerShell.

Les commandes suivantes montrent comment utiliser l’outil DISM à partir de la ligne de commande ou de l’environnement Windows PowerShell. Par défaut, le module PowerShell DISM est inclus dans Windows 8 et Windows Server 2012, et ne doit pas être importé. Pour plus d’informations sur l’utilisation de DISM avec Windows PowerShell, consultez [Guide pratique pour utiliser DISM dans Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).

Pour activer WIF 3.5 à l’aide de DISM :

```console
dism /online /enable-feature:windows-identity-foundation
```

Pour désactiver WIF 3.5 à l’aide de DISM :

```console
dism /online /disable-feature:windows-identity-foundation
```

Pour vérifier les fonctionnalités activées ou désactivées à l’aide de DISM :

```console
dism /online /get-features
```

Vous pouvez également activer WIF 3.5 sur les ordinateurs exécutant Windows Server 2012 à l’aide de l’applet de commande Windows PowerShell `Add-WindowsFeature`. Pour ce faire, à partir de la ligne de commande, vous pouvez entrer la commande suivante :

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 Depuis l’environnement Windows PowerShell, vous pouvez entrer la commande directement :

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> Comme un grand nombre des classes dans WIF 3.5 et WIF 4.5 partagent les mêmes noms, quand vous utilisez WIF 3.5 et WIF 4.5 ensemble, veillez à utiliser des noms de classes qualifiés complets ou des alias d’espaces de noms pour faire la distinction entre les classes dans WIF 3.5 et WIF 4.5.

## <a name="see-also"></a>Voir aussi

- [Schéma de configuration de WIF](../configure-apps/file-schema/windows-identity-foundation/index.md)
- [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Nouveautés de Windows Identity Foundation 4.5](whats-new-in-wif.md)
- [Outil Identité et accès pour Visual Studio 2012](identity-and-access-tool-for-vs.md)
