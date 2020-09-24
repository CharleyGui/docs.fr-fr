---
title: IdentityServer pour les applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: bdf193aac348b54f2ebf5b537beef5d61a1d5a1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163828"
---
# <a name="identityserver-for-cloud-native-applications"></a>IdentityServer pour les applications Cloud natives

IdentityServer est un serveur d’authentification open source qui implémente les normes OpenID Connect (OIDC) et OAuth 2,0 pour ASP.NET Core. Il est conçu pour fournir un moyen courant d’authentifier les demandes à toutes vos applications, qu’il s’agisse de points de terminaison Web, natifs, mobiles ou d’API. IdentityServer peut être utilisé pour implémenter l’authentification unique (SSO) pour plusieurs applications et types d’applications. Il peut être utilisé pour authentifier les utilisateurs réels via des formulaires de connexion et des interfaces utilisateur similaires, ainsi que l’authentification basée sur les services qui implique généralement l’émission, la vérification et le renouvellement de jetons sans aucune interface utilisateur. IdentityServer est conçu pour être une solution personnalisable. Chaque instance est généralement personnalisée pour s’adapter aux besoins d’une organisation et/ou d’un ensemble d’applications.

## <a name="common-web-app-scenarios"></a>Scénarios courants pour les applications Web

En règle générale, les applications doivent prendre en charge tout ou partie des scénarios suivants :

- Utilisateurs humains accédant aux applications Web à l’aide d’un navigateur.
- Utilisateurs humains accédant aux API Web principales à partir d’applications basées sur un navigateur.
- Utilisateurs humains sur des clients mobiles/natifs accédant aux API Web principales.
- Autres applications qui accèdent aux API Web principales (sans utilisateur ou interface utilisateur actif).
- Toute application peut avoir besoin d’interagir avec d’autres API Web, à l’aide de sa propre identité ou en déléguant l’identité de l’utilisateur.

![Types d’application et scénarios](./media/application-types.png)

**Figure 8-1** : Types d’applications et scénarios.

Dans chacun de ces scénarios, la fonctionnalité exposée doit être sécurisée contre toute utilisation non autorisée. Au minimum, cela nécessite généralement l’authentification de l’utilisateur ou du principal qui effectue une demande de ressource. Cette authentification peut utiliser l’un des protocoles courants tels que SAML2p, WS-FED ou OpenID Connect. La communication avec les API utilise généralement le protocole OAuth2 et sa prise en charge des jetons de sécurité. La séparation de ces problèmes critiques de sécurité transversale et de leurs détails d’implémentation à partir des applications elles-mêmes garantit la cohérence et améliore la sécurité et la maintenabilité. L’externalisation de ces préoccupations à un produit dédié comme IdentityServer permet à chaque application de résoudre ces problèmes eux-mêmes.

IdentityServer fournit un intergiciel (middleware) qui s’exécute dans une application ASP.NET Coree et ajoute la prise en charge de OpenID Connect et OAuth2 (voir [spécifications prises en charge](https://docs.identityserver.io/en/latest/intro/specs.html)). Les organisations créent leur propre ASP.NET Core application à l’aide de l’intergiciel (middleware) IdentityServer pour agir en tant que STS pour tous les protocoles de sécurité basés sur les jetons. L’intergiciel IdentityServer expose des points de terminaison pour prendre en charge les fonctionnalités standard, notamment :

- Autoriser (authentifier l’utilisateur final)
- Jeton (demander un jeton par programmation)
- Découverte (métadonnées relatives au serveur)
- Informations utilisateur (obtenir les informations utilisateur avec un jeton d’accès valide)
- Autorisation de l’appareil (utilisée pour démarrer l’autorisation du workflow de l’appareil)
- Inretrospect (validation de jeton)
- Révocation (révocation de jeton)
- Terminer la session (déclencher la déconnexion unique pour toutes les applications)

## <a name="getting-started"></a>Prise en main

IdentityServer4 est open source et gratuit à utiliser. Vous pouvez l’ajouter à vos applications à l’aide de ses packages NuGet. Le package principal est [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) qui a été téléchargé plus de 4 millions fois. Le package de base n’inclut pas de code d’interface utilisateur et ne prend en charge que dans la configuration de la mémoire. Pour l’utiliser avec une base de données, vous devez également disposer d’un fournisseur de données comme [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) qui utilise Entity Framework Core pour stocker les données de configuration et opérationnelles pour IdentityServer. Pour l’interface utilisateur, vous pouvez copier des fichiers à partir du référentiel de l' [interface utilisateur de démarrage rapide](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) dans votre application ASP.net Core MVC pour ajouter la prise en charge de la connexion et de la déconnexion à l’aide de l’intergiciel IdentityServer.

## <a name="configuration"></a>Configuration

IdentityServer prend en charge différents types de protocoles et de fournisseurs d’authentification sociale qui peuvent être configurés dans le cadre de chaque installation personnalisée. En général, cette opération est effectuée dans la classe de l’application ASP.NET Core `Startup` de la `ConfigureServices` méthode. La configuration implique la spécification des protocoles pris en charge et des chemins d’accès aux serveurs et points de terminaison qui seront utilisés. La figure 8-2 montre un exemple de configuration issu du projet d’interface utilisateur de démarrage rapide IdentityServer4 :

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

**Figure 8-2**. Configuration de IdentityServer.

IdentityServer héberge également un site de démonstration public qui peut être utilisé pour tester différents protocoles et configurations. Il se trouve dans [https://demo.identityserver.io/](https://demo.identityserver.io/) et contient des informations sur la façon de configurer son comportement en fonction du `client_id` fourni.

## <a name="javascript-clients"></a>Clients JavaScript

De nombreuses applications Cloud natives exploitent les API côté serveur et les applications à page unique clientes riches sur le serveur frontal. IdentityServer fournit un [client JavaScript](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) via NPM qui peut être ajouté à spas pour lui permettre d’utiliser IdentityServer pour la connexion, la déconnexion et l’authentification basée sur les jetons des API Web.

## <a name="references"></a>Références

- [Documentation IdentityServer](https://docs.identityserver.io/en/latest/)
- [Types d’applications](/azure/active-directory/develop/app-types)
- [Client JavaScript OIDC](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
>[Précédent](azure-active-directory.md) 
> [Suivant](security.md)
