---
title: Schéma des sections de configuration
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441659"
---
# <a name="configuration-sections-schema"></a>Schéma des sections de configuration

Le schéma des sections de configuration contient des éléments qui définissent des paramètres personnalisés dans les fichiers de configuration. Pour obtenir des informations générales sur les fichiers de configuration et les schémas, consultez [schéma du fichier de configuration pour le .NET Framework](index.md).

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | Description |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace de noms. |
| [**\<section>** pour **\<configSections>** et**\<sectionGroup>**](section-element.md) | Contient une déclaration de section de configuration. |
| [**\<sectionGroup>** pour**\<configSections>**](sectiongroup-element-for-configsections.md) | Définit un espace de noms pour les sections de configuration. |

<a name="dep"></a>

## <a name="unimplemented-elements"></a>Éléments non implémentés

Les éléments suivants n’ont aucun impact et ne doivent pas être utilisés :

* **\<clear>**
* **\<remove>**
