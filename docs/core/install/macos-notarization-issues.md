---
title: Travailler avec macOS Catalina Notarization
description: Comment gérer les problèmes de notarisation et de certificat avec macOS lorsque vous installez le temps d’exécution .NET Core, SDK, et les applications construites avec .NET Core.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146747"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Notarization et l’impact sur les téléchargements et projets .NET Core

À partir de macOS Catalina (version 10.15), tous les logiciels construits après le 1er juin 2019 et distribués avec Developer ID, doivent être notariés. Cette exigence s’applique au temps d’exécution .NET Core, .NET Core SDK, et au logiciel créé avec .NET Core. Cet article décrit les scénarios communs que vous pouvez faire face avec .NET Core et macOS notarization.

## <a name="installing-net-core"></a>Installation de .NET Core

Les installateurs pour les versions .NET Core (à la fois en runtime et SDK) 3.1, 3.0 et 2.1, ont été notariés depuis le 18 février 2020. Les versions publiées antérieurement ne sont pas notariées. Vous pouvez installer manuellement une version non notariée de .NET Core en `sudo installer` téléchargeant d’abord l’installateur, puis en utilisant la commande. Pour plus d’informations, voir [Télécharger et installer manuellement pour macOS](sdk.md?pivots=os-macos#download-and-manually-install).

En commençant par les versions suivantes, les installateurs .NET Core sont notariés :

- Runtime .NET Core
  - 2.1.16
  - 3.0.3
  - 3.1.2

- SDK .NET Core
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost est désactivé par défaut

Par défaut, les versions non notariées du .NET Core SDK 3.0 et plus produisent un Mach-O natif exécutable (connu sous le nom **d’appHost**) lorsque votre projet compile, publie ou est exécuté. Cet exécutable est un moyen pratique d’exécuter votre application. Sinon, votre application doit `dotnet <filename.dll>`être lancée en cours d’exécution . Lorsque l’appHost est `dotnet run` activé, la commande est invoquée dans le contexte de l’appHost. Pour plus d’informations, voir [Contexte de l’appHost](#context-of-the-apphost).

En commençant par les versions notariées du .NET Core SDK 3.0 et plus, l’appHost exécutable n’est pas généré par défaut. Vous pouvez activer la génération [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) d’appHost avec le paramètre boolean dans le fichier du projet. Vous pouvez également basculer l’appHost avec le `-p:UseAppHost` paramètre sur la ligne de commande pour la commande spécifique que `dotnet` vous exécutez:

- Fichier projet

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Paramètre de ligne de commande

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Un appHost est toujours créé lorsque vous publiez votre application [autonome](../deploying/index.md#publish-self-contained).

Pour plus d’informations sur le `UseAppHost` paramètre, voir [propriétés MSBuild pour Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Contexte de l’appHost

Lorsque l’appHost est activé dans votre `dotnet run` projet, et que vous utilisez la commande pour exécuter votre application, l’application est `dotnet` invoquée dans le contexte de l’appHost et non l’hôte par défaut (l’hôte par défaut est la commande). Si l’appHost est désactivé `dotnet run` dans votre projet, la commande exécute votre application dans le cadre de l’hôte par défaut. Même si l’appHost est désactivé, la publication de votre application en tant qu’autonome génère une application Host exécutable, et les utilisateurs utilisent celui exécutable pour exécuter votre application. Exécution de `dotnet <filename.dll>` votre application avec invoque l’application avec l’hôte par défaut, l’heure d’exécution partagée.

Lorsqu’une application utilisant l’appHost est invoquée, la partition de certificat consultée par l’application est différente de l’hôte par défaut notarié. Si votre application doit accéder aux certificats installés `dotnet run` via l’hôte par défaut, utilisez `dotnet <filename.dll>` la commande pour exécuter votre application à partir de son fichier de projet, ou utilisez la commande pour démarrer l’application directement.

Plus d’informations sur ce scénario sont fournies dans la section [ASP.NET Core et macOS et certificats.](#aspnet-core-and-macos-and-certificates)

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core et macOS et certificats

.NET Core offre la possibilité de gérer les certificats <xref:System.Security.Cryptography.X509Certificates> dans le macOS Keychain avec la classe. L’accès au macOS Keychain utilise l’identité des applications comme clé principale lors de la décision de la partition à considérer. Par exemple, les applications non signées stockent des secrets dans la partition non signée, mais les applications signées stockent leurs secrets dans des partitions qu’elles peuvent accéder. La source d’exécution qui invoque votre application décide de la partition à utiliser.

.NET Core fournit trois sources d’exécution : `dotnet` [appHost](#apphost-is-disabled-by-default), hôte par défaut (la commande) et hôte personnalisé. Chaque modèle d’exécution peut avoir des identités différentes, signées ou non signées, et a accès à différentes partitions au sein du Keychain. Les certificats importés par un mode peuvent ne pas être accessibles à partir d’un autre. Par exemple, les versions notariées de .NET Core ont un hôte par défaut qui est signé. Les certificats sont importés dans une partition sécurisée en fonction de son identité. Ces certificats ne sont pas accessibles à partir d’une appHost générée, car l’appHost n’est pas signé.

Un autre exemple, par défaut, ASP.NET Core importe un certificat SSL par défaut par l’intermédiaire de l’hôte par défaut. ASP.NET applications de base qui utilisent un appHost n’auront pas accès à ce certificat et recevront une erreur lorsque .NET Core détecte que le certificat n’est pas accessible. Le message d’erreur fournit des instructions sur la façon de résoudre ce problème.

Si le partage de certificat est nécessaire, macOS fournit des options de configuration avec l’utilitaire. `security`

Pour plus d’informations sur la façon de dépanner ASP.NET questions de certificat de base, voir [Enforce HTTPS dans ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Droits par défaut

.NET Core’s default `dotnet` host (la commande) a un ensemble de droits par défaut. Ces droits sont requis pour le bon fonctionnement de .NET Core. Il est possible que votre demande ait besoin de droits supplémentaires, auquel cas vous devrez générer et utiliser une [appHost,](#apphost-is-disabled-by-default) puis ajouter les droits nécessaires localement.

Ensemble de droits par défaut pour .NET Core:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notarize a .NET Core app

Si vous souhaitez que votre application s’exécute sur macOS Catalina (version 10.15) ou plus, vous voudrez notarier votre application. L’appHost que vous soumettez avec votre demande de notarisation doit être utilisé avec au moins les mêmes [droits par défaut](#default-entitlements) pour .NET Core.

## <a name="next-steps"></a>Étapes suivantes

- [.NET Dépendances et exigences](dependencies.md)de base .
- [Installer le .NET Core SDK](sdk.md).
- [Installer le .NET Core Runtime](runtime.md)
