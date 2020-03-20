---
title: <clear>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155425"
---
# <a name="clear-element-for-configsections"></a>\<un élément clair> \<pour les> de configSections

Efface toutes les sections et les groupes de section précédemment définis.

&nbsp; &nbsp; &nbsp; &nbsp; ** \<** [**les \<**](configuration-element.md) [**>les configections>claires>\<**](configsections-element-for-configuration.md) &nbsp; &nbsp;

## <a name="syntax"></a>Syntaxe

```xml
<clear/>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom de la section ou du groupe de section à supprimer. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [les>des configections ** \<** Élément](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace nom. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes 

** \<L’élément>clair** supprime toutes les sections et les groupes de section de votre application qui ont été définis plus tôt dans le fichier de configuration actuel ou à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a> Exemple

Cet exemple définit un fichier de configuration de machine et un fichier de configuration d’application et montre comment utiliser ** \<l’élément>clair** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de la machine.

Le code de fichier de configuration de la machine suivante ** \< **déclare deux sections, ** \<l’échantillonSection>** et un autre>de la configuration de la machine, qui sont lus avant le fichier de configuration d’application :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

Le code de fichier de configuration d’application suivant efface toutes les sections précédemment déclarées. L’application ne peut pas utiliser ou récupérer les paramètres dans l’une ou l’autre des sections qui ont été déclarées dans le fichier de configuration de la machine. Cependant, il peut utiliser les paramètres ** \<d’un autre>** de la section parce qu’il vient après ** \<l’élément clair>.**

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](index.md)
