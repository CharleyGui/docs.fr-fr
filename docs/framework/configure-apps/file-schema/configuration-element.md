---
title: <configuration>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921244"
---
# <a name="configuration-element"></a>\<élément de > de configuration

Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.

**\<configuration>**

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Attributs

Aucun

## <a name="parent-element"></a>Élément parent

Aucun

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) | Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.|
| [schéma des paramètres de démarrage >  **\<** ](./startup/index.md) | Tous les éléments du schéma des paramètres de démarrage. |
| [schéma des paramètres de > du runtime  **\<** ](./runtime/index.md) | Tous les éléments du schéma des paramètres d’exécution. |
| [schéma des paramètres de **> System. Runtime. Remoting \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Tous les éléments du schéma des paramètres de communication à distance. |
| [schéma des paramètres **System .net > \<** ](./network/index.md) | Tous les éléments du schéma des paramètres réseau. |
| [schéma des paramètres de > cryptographySettings  **\<** ](./cryptography/index.md) | Tous les éléments du schéma des paramètres de chiffrement. |
| [schéma des sections de > de configuration  **\<** ](configuration-sections-schema.md) | Tous les éléments du schéma des paramètres de la section de configuration. |
| [Schéma des paramètres de trace et de débogage](./trace-debug/index.md) | Tous les éléments du schéma des paramètres de trace et de débogage. |
| [Schéma des paramètres de configuration de ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Tous les éléments du schéma de configuration ASP.NET, qui incluent des éléments pour la configuration des applications et des sites Web ASP.NET. Utilisé dans les fichiers *Web. config* . |
| [schéma des paramètres WebServices >  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Tous les éléments du schéma des paramètres des services Web. |
| [Schéma des paramètres web](./web/index.md) | Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS. Utilisé dans les fichiers *Aspnet. config* . |

## <a name="remarks"></a>Notes

Chaque fichier de configuration doit contenir exactement  **\<** un élément de configuration >.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
