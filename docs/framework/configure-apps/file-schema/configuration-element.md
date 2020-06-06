---
title: <configuration> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921244"
---
# <a name="configuration-element"></a>\<configuration>, élément

Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.

**\<configuration>**

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Attributs

Aucune

## <a name="parent-element"></a>Élément parent

Aucune

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.|
| [**\<startup>** Schéma des paramètres](./startup/index.md) | Tous les éléments du schéma des paramètres de démarrage. |
| [**\<runtime>** Schéma des paramètres](./runtime/index.md) | Tous les éléments du schéma des paramètres d’exécution. |
| [**\<system.runtime.remoting>** Schéma des paramètres](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Tous les éléments du schéma des paramètres de communication à distance. |
| [**\<system.Net>** Schéma des paramètres](./network/index.md) | Tous les éléments du schéma des paramètres réseau. |
| [**\<cryptographySettings>** Schéma des paramètres](./cryptography/index.md) | Tous les éléments du schéma des paramètres de chiffrement. |
| [**\<configuration>** Schéma des sections](configuration-sections-schema.md) | Tous les éléments du schéma des paramètres de la section de configuration. |
| [Schéma des paramètres de traçage et de débogage](./trace-debug/index.md) | Tous les éléments du schéma des paramètres de trace et de débogage. |
| [Schéma des paramètres de configuration de ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Tous les éléments du schéma de configuration ASP.NET, qui incluent des éléments pour la configuration des applications et des sites Web ASP.NET. Utilisé dans les fichiers *Web. config* . |
| [**\<webServices>** Schéma des paramètres](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Tous les éléments du schéma des paramètres des services Web. |
| [Schéma des paramètres web](./web/index.md) | Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS. Utilisé dans les fichiers *Aspnet. config* . |

## <a name="remarks"></a>Remarques

Chaque fichier de configuration doit contenir exactement un **\<configuration>** élément.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
