---
title: Nouveautés de Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 93631c1171f81ec8b8d94b56a56012343f6c3220
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045280"
---
# <a name="whats-new-in-windows-identity-foundation-45"></a>Nouveautés de Windows Identity Foundation 4.5
La première version de Windows Identity Foundation (WIF) était fournie sous forme de téléchargement autonome et s'appelait WIF 3.5 car elle a été introduite dans le calendrier SP1 de .NET 3.5. Depuis la version .NET 4.5, WIF fait partie de .NET framework. Le fait d’avoir les classes WIF directement disponibles dans l’infrastructure permet une meilleure intégration de l’identité basée sur les revendications dans .NET, facilitant ainsi l’utilisation des revendications. Les applications écrites pour WIF 3.5 doivent être modifiées pour tirer parti du nouveau modèle. Pour plus d’informations, consultez [Instructions pour migrer une application WIF 3.5 en application WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Vous trouverez ci-dessous certaines indications sur les principales modifications.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF fait désormais partie de .NET Framework  
 Les classes WIF sont désormais réparties sur plusieurs assemblys, les principales étant `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, et `System.ServiceModel`. De même, les classes WIF sont réparties dans plusieurs espaces de noms : <xref:System.Security.Claims?displayProperty=nameWithType>, certains espaces de noms [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004), et <xref:System.ServiceModel.Security?displayProperty=nameWithType>. L'espace de noms <xref:System.Security.Claims?displayProperty=nameWithType> contient les nouvelles classes <xref:System.Security.Claims.ClaimsPrincipal> et <xref:System.Security.Claims.ClaimsIdentity> (voir ci-dessous). Toutes les entités du .NET dérivent maintenant de <xref:System.Security.Claims.ClaimsPrincipal>. Pour plus d’informations sur les espaces de noms WIF et les types de classes qu’ils contiennent, consultez [Informations de référence sur l’API WIF](wif-api-reference.md). Pour plus d’informations sur la façon dont les espaces de noms WIF 3.5 et WIF 4.5 sont mappés, consultez [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nouveaux modèles de revendication et Objet principal  
 Les revendications représentent la caractéristique principale de .NET Framework 4.5. Toutes les classes de revendication de base (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, et <xref:System.Security.Claims.ClaimValueTypes>) sont directement actives dans `mscorlib` et dans l'espace de noms <xref:System.Security.Claims?displayProperty=nameWithType>. Il n'est plus nécessaire d'utiliser des interfaces pour insérer des revendications dans le système d'identité .NET : <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, et <xref:System.Web.Security.RolePrincipal> héritent maintenant de <xref:System.Security.Claims.ClaimsPrincipal>; et <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, et <xref:System.Web.Security.FormsIdentity> héritent maintenant de <xref:System.Security.Claims.ClaimsIdentity>. En bref, chaque classe principale servira à présent les revendications. Les classes d'intégration et les interfaces WIF 3.5 (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) et ont été supprimées. En outre, la classe <xref:System.Security.Claims.ClaimsIdentity> expose maintenant des méthodes qui facilitent l’interrogation de la collection des revendications d’identité.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Modifications apportées à l'expérience WIF Visual Studio 4.5  
  
- La fonctionnalité **Ajouter référence STS…** (utilitaire cmdline FedUtil) de Visual Studio n’existe plus. À la place, utilisez la nouvelle extension **Identity and Access Tool pour Visual Studio 2012** disponible dans Visual Studio. Cela vous permet de vous fédérer avec un STS existant ou d'utiliser LocalSTS pour tester vos solutions. Après avoir installé l’extension, cliquez avec le bouton droit sur votre projet et recherchez **Identity and Access** dans le menu contextuel.  
  
- Les modèles ASP.NET et STS ne sont plus fournis car les revendications peuvent être utilisées directement dans les modèles de projet existants pour ASP.Net, les sites Web, et WCF.  
  
- Les contrôles de l'espace de noms `Microsoft.IdentityModel.Web.Controls` (`SignInControl`, `FederatedPassiveSignInControl`, et `FederatedPassiveSignInStatus`) ne sont pas retenus dans WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Modifications apportées à l'API WIF 4.5  
  
- En général, les classes associées aux revendications se trouvent dans l’espace de noms <xref:System.Security.Claims?displayProperty=nameWithType> ; les classes associées à WCF (contrats de service, canaux, fabriques de canaux et hôtes de service utilisés dans des scénarios WS-Trust) se trouvent dans les espaces de noms <xref:System.ServiceModel.Security?displayProperty=nameWithType> ; et toutes les autres classes WIF sont réparties dans différents espaces de noms [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) (il s’agit notamment des classes représentant des artefacts WS-* et SAML, des gestionnaires de jetons et les classes associées, ainsi que des classes utilisées dans les scénarios WS-Federation). Pour plus d’informations, consultez [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md) et [Informations de référence sur l’API WIF](wif-api-reference.md).  
  
- La clé de l'ordinateur a été activée pour une utilisation dans des cookies de session pour les scénarios de batterie de serveurs Web. Pour plus d’informations, consultez [WIF et batteries de serveurs Web](wif-and-web-farms.md).  
  
- Vous configurez maintenant WIF de manière déclarative sous les éléments [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) et [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). Pour plus d’informations sur la configuration de WIF, consultez [Informations de référence sur la configuration de WIF](wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Autres modifications notables .NET ou fonctionnalités causées par l'intégration de WIF dans .NET  
  
- La possibilité d'effectuer des autorisations basées sur les revendications est maintenant intégrée dans .NET framework. Vous pouvez configurer un objet <xref:System.Security.Claims.ClaimsAuthorizationManager>, puis utiliser les classes <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> et <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> pour effectuer les vérifications d'accès impératives et déclaratives dans votre code. CBAC offre plus de souplesse et de granularité que les vérifications requises en matière d'accès basée sur des rôles. Il permet également une séparation plus nette entre la stratégie d’autorisation et la logique métier. En effet, la logique métier peut être basée sur la vérification de l’accès sur une revendication spécifique ou un ensemble de revendications, et la stratégie d’autorisation pour ces revendications peut être configurée de façon déclarative dans l’élément [\<claimsAuthorizationManager>](../configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md).  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Modifications apportées à WCF suite à l'intégration de WIF :  
  
- Le modèle d'identité basé sur des revendications WCF est remplacé par WIF. Cela signifie que les classes de <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> et les espaces de noms <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> doivent être supprimés et remplacés afin d’utiliser des classes de WIF.  
  
- Vous activez maintenant WIF sur un service WCF en spécifiant l’attribut `useIdentityConfiguration` sur l’élément `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` comme dans le code XML suivant :  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Si vous utilisez **Identity and Access Tool pour Visual Studio 2012** (consultez **Modifications apportées à l’expérience Visual Studio** ci-dessus), l’outil ajoute un élément `<serviceCredentials>` avec l’attribut `useIdentityConfiguration` automatiquement défini sur le fichier de configuration. Il ajoute également un élément [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) correspondant qui contient les paramètres de configuration WI, ainsi qu’une liaison et d’autres paramètres nécessaires pour externaliser l’authentification au STS choisi.  
  
## <a name="see-also"></a>Voir aussi

- [Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
- [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Référence de l’API WIF](wif-api-reference.md)
- [Référence de configuration de WIF](wif-configuration-reference.md)
