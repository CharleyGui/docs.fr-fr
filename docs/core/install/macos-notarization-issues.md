---
title: Utilisation de la notaire Catalina macOS
description: Gestion des problèmes de notaire et de certificat avec macOS quand vous installez le Runtime .NET Core, le kit de développement logiciel (SDK) et les applications créées avec .NET Core.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: b16ef4074f829246df0aedebf7ffe4df75faed51
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78165364"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>la notaire Catalina macOS et l’impact sur les téléchargements et les projets .NET Core

À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019 et distribués avec l’ID de développeur doivent être certifiés. Cette exigence s’applique au Runtime .NET Core, kit SDK .NET Core et aux logiciels créés avec .NET Core. Cet article décrit les scénarios courants que vous pouvez rencontrer avec la notaire .NET Core et macOS.

## <a name="installing-net-core"></a>Installation de .NET Core

Les programmes d’installation de .NET Core (Runtime et SDK) versions 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020. Les versions antérieures publiées ne sont pas certifiées. Vous pouvez installer manuellement une version non certifiée de .NET Core en téléchargeant d’abord le programme d’installation, puis en utilisant la commande `sudo installer`. Pour plus d’informations, consultez [Télécharger et installer manuellement pour MacOS](sdk.md?pivots=os-macos#download-and-manually-install).

À partir des versions suivantes, les programmes d’installation de .NET Core sont certifiés :

- Runtime .NET Core
  - 2.1.16
  - 3.0.3
  - 3.1.2

- SDK .NET Core
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost est désactivé par défaut

Par défaut, les versions non certifiées des kit SDK .NET Core 3,0 et ultérieures produisent un exécutable Mach-O natif (connu sous le nom de **apphost**) lorsque votre projet compile, publie ou est exécuté. Cet exécutable est un moyen pratique d’exécuter votre application. Dans le cas contraire, votre application doit être démarrée en exécutant `dotnet <filename.dll>`. Lorsque le appHost est activé, la commande `dotnet run` est appelée dans le contexte de appHost. Pour plus d’informations, consultez [Context of the apphost](#context-of-the-apphost).

À compter de la version certifiée des kit SDK .NET Core 3,0 et versions ultérieures, l’exécutable appHost n’est pas généré par défaut. Vous pouvez activer la génération de appHost avec le paramètre booléen [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) dans le fichier projet. Vous pouvez également basculer le appHost avec le paramètre `-p:UseAppHost` sur la ligne de commande pour la commande `dotnet` spécifique que vous exécutez :

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

Pour plus d’informations sur le paramètre `UseAppHost`, consultez [propriétés MSBuild pour Microsoft. net. SDK](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Contexte de appHost

Lorsque le appHost est activé dans votre projet et que vous utilisez la commande `dotnet run` pour exécuter votre application, l’application est appelée dans le contexte du appHost et non de l’hôte par défaut (l’hôte par défaut est la commande `dotnet`). Si le appHost est désactivé dans votre projet, la commande `dotnet run` exécute votre application dans le contexte de l’hôte par défaut. Même si le appHost est désactivé, la publication de votre application comme autonome génère un fichier exécutable appHost, et les utilisateurs utilisent ce fichier exécutable pour exécuter votre application. L’exécution de votre application avec `dotnet <filename.dll>` appelle l’application avec l’hôte par défaut, le runtime partagé.

Lorsqu’une application utilisant appHost est appelée, la partition de certificat accessible par l’application est différente de l’hôte par défaut authentifié. Si votre application doit accéder aux certificats installés par le biais de l’hôte par défaut, utilisez la commande `dotnet run` pour exécuter votre application à partir de son fichier projet ou utilisez la commande `dotnet <filename.dll>` pour démarrer l’application directement.

Des informations supplémentaires sur ce scénario sont fournies dans la section [ASP.net Core et MacOS et Certificates](#aspnet-core-and-macos-and-certificates) .

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core et macOS et certificats

.NET Core offre la possibilité de gérer des certificats dans le trousseau macOS avec la classe <xref:System.Security.Cryptography.X509Certificates>. L’accès au trousseau macOS utilise l’identité des applications comme clé primaire pour déterminer la partition à prendre en compte. Par exemple, les applications non signées stockent des secrets dans la partition non signée, mais les applications signées stockent leurs secrets dans des partitions auxquelles seules elles peuvent accéder. La source d’exécution qui appelle votre application détermine la partition à utiliser.

.NET Core fournit trois sources d’exécution : [apphost](#apphost-is-disabled-by-default), l’hôte par défaut (commande `dotnet`) et un hôte personnalisé. Chaque modèle d’exécution peut avoir des identités différentes, signées ou non signées, et a accès à différentes partitions dans le trousseau. Les certificats importés par un mode peuvent ne pas être accessibles à partir d’un autre. Par exemple, les versions certifiées de .NET Core ont un hôte par défaut qui est signé. Les certificats sont importés dans une partition sécurisée en fonction de son identité. Ces certificats ne sont pas accessibles à partir d’un appHost généré, car le appHost n’est pas signé.

Un autre exemple, par défaut, ASP.NET Core importe un certificat SSL par défaut par le biais de l’hôte par défaut. ASP.NET Core applications qui utilisent un appHost n’ont pas accès à ce certificat et recevront une erreur quand .NET Core détecte que le certificat n’est pas accessible. Le message d’erreur fournit des instructions sur la façon de résoudre ce problème.

Si le partage de certificats est requis, macOS fournit des options de configuration avec l’utilitaire `security`.

Pour plus d’informations sur la résolution des problèmes liés aux certificats de ASP.NET Core, consultez [appliquer https dans ASP.net Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Droits par défaut

L’hôte par défaut de .NET Core (commande `dotnet`) a un ensemble de droits par défaut. Ces droits sont requis pour le bon fonctionnement de .NET Core. Il est possible que votre application ait besoin de droits supplémentaires. dans ce cas, vous devrez générer et utiliser un [apphost](#apphost-is-disabled-by-default) , puis ajouter les droits nécessaires localement.
 
Ensemble par défaut des droits pour .NET Core :

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notaire une application .NET Core

Si vous souhaitez que votre application s’exécute sur macOS Catalina (version 10,15) ou une version ultérieure, vous souhaiterez que votre application soit authentifiée. Le appHost que vous envoyez avec votre application pour la notaire doit être utilisé avec au moins les mêmes [droits par défaut](#default-entitlements) pour .net core.

## <a name="next-steps"></a>Étapes suivantes :

- [Dépendances et exigences .net Core](dependencies.md).
- [Installez le kit SDK .net Core](sdk.md).
- [Installer le Runtime .NET Core](runtime.md)
