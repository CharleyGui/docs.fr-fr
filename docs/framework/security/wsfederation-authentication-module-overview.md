---
title: Vue d’ensemble du module d’authentification WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: eaf53a352238161ccec1b481649074d322954905
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851504"
---
# <a name="wsfederation-authentication-module-overview"></a>Vue d’ensemble du module d’authentification WSFederation
Windows Identity Foundation (WIF) prend en charge l’authentification fédérée dans les applications ASP.NET par le biais du module WS-FAM (WS-Federated Authentication Module). Cette rubrique explique le fonctionnement et l’utilisation de l’authentification fédérée.  
  
### <a name="overview-of-federated-authentication"></a>Vue d’ensemble de l’authentification fédérée  
 L’authentification fédérée permet à un service d’émission de jeton de sécurité (STS) dans un domaine d’approbation de fournir des informations d’authentification à un STS situé dans un autre domaine d’approbation avec lequel il a une relation d’approbation. Vous en trouverez un exemple dans l’illustration suivante :  
  
 ![Diagramme montrant le scénario d’authentification fédérée.](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Un client situé dans le domaine d’approbation Fabrikam envoie une demande à une application par partie de confiance qui se trouve dans le domaine d’approbation Contoso.  
  
2. La partie de confiance redirige le client vers un STS du domaine d’approbation Contoso. Ce STS ne connaît pas le client.  
  
3. Le STS Contoso redirige le client vers un STS situé dans le domaine d’approbation Fabrikam, avec lequel le domaine d’approbation Contoso a une relation d’approbation.  
  
4. Le STS Fabrikam vérifie l’identité du client et envoie un jeton de sécurité au STS Contoso.  
  
5. Le STS Contoso utilise le jeton Fabrikam pour créer son propre jeton utilisable par la partie de confiance et l’envoie à celle-ci.  
  
6. La partie de confiance extrait les revendications du client à partir du jeton de sécurité et rend une décision d’autorisation.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Utilisation du module d’authentification fédérée avec ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-FAM) est un module HTTP qui vous permet d’ajouter une authentification fédérée à une application ASP.NET. Grâce à l’authentification fédérée, la logique d’authentification est gérée par le STS. Vous pouvez ainsi vous concentrer sur le travail d’écriture de la logique métier.  
  
 Vous configurez le module WS-FAM pour spécifier le STS vers lequel les demandes non authentifiées doivent être redirigées. WIF vous permet d’authentifier un utilisateur selon deux méthodes :  
  
1. Redirection passive : Lorsqu’un utilisateur non authentifié tente d’accéder à une ressource protégée et que vous souhaitez simplement le rediriger vers un STS sans avoir besoin d’une page de connexion, il s’agit de la bonne approche. Le STS vérifie l’identité de l’utilisateur et émet un jeton de sécurité qui contient les revendications appropriées pour cet utilisateur. Cette méthode nécessite l’ajout du module WS-FAM dans le pipeline des modules HTTP. L’outil Identity and Access pour Visual Studio 2012 vous permet de modifier le fichier de configuration de votre application afin d’utiliser le module WS-FAM et la fédération avec un STS. Pour plus d’informations, consultez [Identity and Access Tool pour Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2. Vous pouvez appeler la méthode <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> ou la méthode <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> à partir du code-behind pour afficher une page de connexion dans votre application par partie de confiance.  
  
 Avec la redirection passive, toutes les communications sont effectuées par réponse/redirection du client (en général, un navigateur). Vous pouvez ajouter le module WS-FAM au pipeline HTTP de votre application, où il surveille les demandes d’utilisateurs non authentifiés et redirige ces utilisateurs vers le STS que vous spécifiez.  
  
 Le module WS-FAM déclenche également plusieurs événements qui vous permettent de personnaliser ses fonctionnalités dans une application ASP.NET.  
  
### <a name="how-the-ws-fam-works"></a>Fonctionnement du module WS-FAM  
 Le module WS-FAM est implémenté dans la classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>. En règle générale, vous ajoutez le WS-FAM au pipeline HTTP de votre application ASP.NET RP. Quand un utilisateur non authentifié tente d’accéder à une ressource protégée, la partie de confiance retourne une réponse HTTP de type « Erreur 401 : autorisation refusée ». Le module WS-FAM intercepte cette réponse avant qu’elle soit reçue par le client, puis il redirige l’utilisateur vers le STS spécifié. Le STS émet un jeton de sécurité, que le module WS-FAM intercepte encore. Le WS-FAM utilise le jeton pour créer une instance de <xref:System.Security.Claims.ClaimsPrincipal> pour l’utilisateur authentifié, ce qui permet aux mécanismes d’autorisation .NET Framework standard de fonctionner.  
  
 Étant donné que le protocole HTTP est sans état, vous devez empêcher la répétition de ce processus à chaque tentative de l’utilisateur d’accéder à une ressource protégée. Pour cela, utilisez <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Quand le STS émet un jeton de sécurité pour l’utilisateur, <xref:System.IdentityModel.Services.SessionAuthenticationModule> crée également un jeton de sécurité de session pour l’utilisateur et le place dans un cookie. Lors des demandes suivantes, <xref:System.IdentityModel.Services.SessionAuthenticationModule> intercepte ce cookie et l’utilise pour reconstruire le <xref:System.Security.Claims.ClaimsPrincipal> de l’utilisateur.  
  
 Le diagramme suivant illustre le flux global des données dans le cas de la redirection passive. La demande est automatiquement redirigée via le STS pour spécifier les informations d’identification sans passer par une page de connexion :  
  
 ![Diagramme illustrant la connexion avec redirection passive.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Le diagramme suivant détaille ce qui se passe quand l’utilisateur est authentifié auprès du STS et que ses jetons de sécurité sont traités par <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> :  
  
 ![Minutage du traitement des jetons avec la redirection passive](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Le diagramme suivant montre en détail ce qui se passe quand les jetons de sécurité de l’utilisateur ont été sérialisés dans des cookies, puis interceptés par <xref:System.IdentityModel.Services.SessionAuthenticationModule> :  
  
 ![Diagramme de minutage SAM de la connexion avec des contrôles](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Events  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule> et leur classe parente <xref:System.IdentityModel.Services.HttpModuleBase> déclenchent des événements à différentes étapes du traitement d’une requête HTTP. Vous pouvez gérer ces événements dans le `global.asax` fichier de votre application ASP.net.  
  
- L’infrastructure ASP.NET appelle la méthode <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> du module pour initialiser le module.  
  
- L’événement <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> est déclenché quand l’infrastructure ASP.NET appelle la méthode <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> pour la première fois sur l’un des modules de l’application qui dérivent de <xref:System.IdentityModel.Services.HttpModuleBase>. Cette méthode accède à la propriété <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> statique, qui spécifie le chargement de la configuration à partir du fichier Web.config. Cet événement est déclenché uniquement lors du premier accès à cette propriété. L’objet <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> initialisé à partir de la configuration est accessible par le biais de la propriété <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> dans un gestionnaire d’événements. Vous pouvez utiliser cet événement pour modifier la configuration avant de l’appliquer aux modules. Vous pouvez ajouter un gestionnaire pour cet événement dans la méthode Application_Start :  
  
    ```csharp
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Chaque module substitue les méthodes abstraites <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> et <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType>. La première de ces méthodes ajoute des gestionnaires pour les événements de pipeline ASP.NET qui sont pertinents pour le module. Dans la plupart des cas, l’implémentation par défaut du module est suffisante. La seconde méthode initialise les propriétés du module à partir de sa propriété <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType>. (Il s’agit d’une copie de la configuration ayant déjà été chargée.) Vous devrez substituer cette deuxième méthode si vous souhaitez autoriser l’initialisation de nouvelles propriétés à partir de la configuration dans les classes que vous dérivez de <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Pour la prise en charge des propriétés de configuration supplémentaires, vous devrez également les dériver à partir des objets de configuration appropriés, par exemple <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> ou <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
- Le module WS-FAM déclenche l’événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> quand il intercepte un jeton de sécurité ayant été émis par le STS.  
  
- Le module WS-FAM déclenche l’événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> une fois qu’il a validé le jeton.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> déclenche l’événement <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> quand il crée un jeton de sécurité de session pour l’utilisateur.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> déclenche l’événement <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> quand il intercepte d’autres demandes avec le cookie contenant le jeton de sécurité de session.  
  
- Avant de rediriger l’utilisateur vers l’émetteur, le module WS-FAM déclenche l’événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>. La demande de connexion de WS-Federation est disponible via la propriété <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> du <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> passé dans l’événement. Vous pouvez modifier la demande avant de l’envoyer à l’émetteur.  
  
- Le module WS-FAM déclenche l’événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> une fois que le cookie a été écrit et que l’utilisateur est connecté.  
  
- Le module WS-FAM déclenche l’événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> une seule fois par session, au moment de la fermeture de la session de chaque utilisateur. Cet événement n’est pas déclenché si la session est fermée côté client (par exemple, en supprimant le cookie de session). Dans un environnement SSO, l’IP/STS peut également demander à chaque partie de confiance de se déconnecter. Cela déclenche aussi cet événement, avec <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> défini sur `true`.  
  
> [!NOTE]
> Vous ne devez pas utiliser la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> pendant un événement déclenché par <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou <xref:System.IdentityModel.Services.SessionAuthenticationModule>. La raison est que la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> est définie après le processus d’authentification, alors que les événements sont déclenchés pendant le processus d’authentification.  
  
### <a name="configuration-of-federated-authentication"></a>Configuration de l’authentification fédérée  
 Les modules WS-FAM et SAM sont configurés à l’aide de l’élément [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md). L’élément enfant [\<wsFederation>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) configure les valeurs par défaut des propriétés de WS-FAM, telles que <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> et <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A>. (Ces valeurs peuvent être modifiées pour chaque demande en fournissant des gestionnaires pour certains événements WS-FAM, comme <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Le gestionnaire de cookies utilisé par le module SAM est configuré à l’aide de l’élément enfant [\<cookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md). WIF fournit un gestionnaire de cookies par défaut implémenté dans la classe <xref:System.IdentityModel.Services.ChunkedCookieHandler> dont la taille de bloc est définie avec l’élément [\<chunkedCookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md). L’élément `<federationConfiguration>` fait référence à un <xref:System.IdentityModel.Configuration.IdentityConfiguration>, qui fournit la configuration d’autres composants WIF utilisés dans l’application, tels que <xref:System.Security.Claims.ClaimsAuthenticationManager> et <xref:System.Security.Claims.ClaimsAuthorizationManager>. La configuration d’identité peut être référencée explicitement en spécifiant un élément [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) nommé dans l’attribut `identityConfigurationName` de l’élément `<federationConfiguration>`. Si la configuration d’identité n’est pas explicitement référencée, la configuration d’identité par défaut est utilisée.  
  
 Le code XML suivant montre une configuration d’une application par partie de confiance ASP.NET. Les sections de configuration <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> et <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sont ajoutées sous l’élément `<configSections>`. Les modules SAM et WS-FAM sont ajoutés aux modules HTTP sous l’élément `<system.webServer>`/`<modules>`. Enfin, les composants WIF sont configurés sous les éléments `<system.identityModel>`/`<identityConfiguration>` et `<system.identityModel.services>`/`<federationConfiguration>`. Cette configuration spécifie le gestionnaire de cookies en bloc, car il s’agit du gestionnaire de cookies par défaut et il n’y a pas de type de gestionnaire de cookies spécifié dans l’élément `<cookieHandler>`.  
  
> [!WARNING]
> Dans l’exemple suivant, l’attribut `requireHttps` de l’élément `<wsFederation>` et l’attribut `requireSsl` de l’élément `<cookieHandler>` ont tous les deux la valeur `false`. Cela présente une menace potentielle pour la sécurité. Dans votre code de production, vous devez définir ces deux valeurs sur `true`.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
