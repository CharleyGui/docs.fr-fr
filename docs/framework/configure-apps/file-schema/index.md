---
title: Schéma des fichiers de configuration pour le .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921025"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma des fichiers de configuration pour le .NET Framework

Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications. Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications. La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.

Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez l’article [Configuration d’applications](../index.md). Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.

> [!IMPORTANT]
> Les étiquettes et attributs XML des fichiers de configuration respectent la casse.

## <a name="in-this-section"></a>Dans cette section

[ **\<configuration>** , élément](configuration-element.md) Décrit l’élément `<configuration>`, qui constitue l’élément de niveau supérieur de tous les fichiers de configuration.

[ **\<assemblyBinding>** , élément](assemblybinding-element-for-configuration.md) Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.

[ **\<linkedConfiguration>** , élément](linkedconfiguration-element.md) Spécifie un fichier de configuration à inclure.

[Schéma des paramètres de démarrage](./startup/index.md) Décrit les éléments qui spécifient la version du common language runtime à utiliser.

[Schéma des paramètres d’exécution](./runtime/index.md) Décrit les éléments qui configurent les liaisons d’assembly et le comportement au moment de l’exécution.

[Schéma des paramètres réseau](./network/index.md) Décrit les éléments qui spécifient la manière dont le .NET Framework se connecte à Internet.

[Schéma des paramètres de chiffrement](./cryptography/index.md) Décrit des éléments qui mappent des noms d’algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.

[Schéma des sections de configuration](configuration-sections-schema.md) Décrit les éléments qui servent à créer et à utiliser les sections de configuration pour les paramètres personnalisés.

[Schéma des paramètres de traçage et de débogage](./trace-debug/index.md) Décrit les éléments qui spécifient les commutateurs et les écouteurs de traçage.

[Schéma des paramètres du fournisseur de langage et du compilateur](./compiler/index.md) Décrit les éléments qui spécifient la configuration de compilateur pour les fournisseurs de langages disponibles.

[Schéma des paramètres d’application](application-settings-schema.md) Décrit les éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.

[Schéma des paramètres d’application](./appsettings/index.md) Contient des paramètres d’application personnalisés, tels que des chemins de fichier, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.

[Schéma des paramètres web](./web/index.md) Tous les éléments du schéma des paramètres web, qui inclut des éléments pour la configuration d’ASP.NET en vue d’une utilisation avec une application hôte telle qu’IIS. Utilisé dans les fichiers *Aspnet.config*.

[Schéma de configuration Windows Forms](winforms/index.md) Tous les éléments de la section de configuration d’application Windows Forms, qui inclut les personnalisations telles que de la prise en charge de plusieurs moniteurs et de la haute résolution.

[Schéma de configuration WCF](./wcf/index.md) Tous les éléments qui vous permettent de configurer les applications clientes et le service WCF.

[Syntaxe de directive WCF](./wcf-directive/index.md) Décrit la directive `@ServiceHost`, qui définit des attributs spécifiques de la page utilisés par le compilateur .svc.

[Schéma de configuration WIF](windows-identity-foundation/index.md) Tous les éléments du schéma de configuration Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Rubriques connexes

[Schéma des paramètres de communication à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Décrit les éléments qui configurent les applications clientes et serveur qui implémentent la communication à distance.

[Schéma de paramètres ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Décrit les éléments qui contrôlent le comportement des applications web ASP.NET.

[Schéma des paramètres des services Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.

[Configuration d’applications .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.
