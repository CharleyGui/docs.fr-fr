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
ms.openlocfilehash: ab6f12be01899f5b7e54a7ec2d9675d502d88bc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555131"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma des fichiers de configuration pour le .NET Framework

Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications. Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications. La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.

Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez [configurer des applications](../index.md). Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.

> [!IMPORTANT]
> Les étiquettes et attributs XML des fichiers de configuration respectent la casse.

## <a name="in-this-section"></a>Contenu de cette section

[**\<configuration>** Appartient](configuration-element.md)\
Élément de niveau supérieur pour tous les fichiers de configuration.

[**\<assemblyBinding>** Appartient](assemblybinding-element-for-configuration.md)\
Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.

[**\<linkedConfiguration>** Appartient](linkedconfiguration-element.md)\
Spécifie un fichier de configuration à inclure.

[Schéma des paramètres de démarrage](./startup/index.md)\
Éléments qui spécifient la version du common language runtime à utiliser.

[Schéma des paramètres d’exécution](./runtime/index.md)\
Éléments qui configurent la liaison d’assembly et le comportement au moment de l’exécution.

[Schéma des paramètres réseau](./network/index.md)\
Éléments qui spécifient la façon dont le .NET Framework se connecte à Internet.

[Schéma des paramètres de chiffrement](./cryptography/index.md)\
Éléments qui mappent des noms d’algorithmes conviviaux aux classes qui implémentent des algorithmes de chiffrement.

[Schéma des sections de configuration](configuration-sections-schema.md)\
Éléments utilisés pour créer et utiliser des sections de configuration pour les paramètres personnalisés.

[Schéma des paramètres de trace et de débogage](./trace-debug/index.md)\
Éléments qui spécifient des commutateurs de trace et des écouteurs.

[Schéma des paramètres du fournisseur de langage et du compilateur](./compiler/index.md)\
Éléments qui spécifient la configuration du compilateur pour les fournisseurs de langages disponibles.

[Schéma des paramètres de l’application](application-settings-schema.md)\
Éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.

[Schéma des paramètres de l’application](./appsettings/index.md)\
Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.

[Schéma des paramètres Web](./web/index.md)\
Éléments permettant de configurer la façon dont ASP.NET fonctionne avec une application hôte telle qu’IIS. Utilisé dans les fichiers *Aspnet.config*.

[Schéma de configuration de Windows Forms](winforms/index.md)\
Tous les éléments de la section de configuration de l’application Windows Forms, qui comprend des personnalisations telles que la prise en charge de plusieurs moniteurs et de la haute résolution.

[Schéma de configuration WCF](./wcf/index.md)\
Tous les éléments qui vous permettent de configurer les applications clientes et de service WCF.

[Syntaxe de directive WCF](./wcf-directive/index.md)\
Décrit la `@ServiceHost` directive, qui définit des attributs spécifiques à la page utilisés par le compilateur. svc.

[Schéma de configuration de WIF](windows-identity-foundation/index.md)\
Tous les éléments du schéma de configuration de Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Sections connexes

[Schéma des paramètres de communication à distance](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\
Décrit les éléments qui configurent les applications client-serveur qui implémentent la communication à distance.

[Schéma des paramètres ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\
Décrit les éléments qui contrôlent le comportement d'applications web ASP.NET.

[Schéma des paramètres des services Web](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\
Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.

[Configuration des applications .NET Framework](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.
