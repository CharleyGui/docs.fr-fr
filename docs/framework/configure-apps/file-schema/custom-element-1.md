---
title: Élément personnalisé pour SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 0d765a9789ad566428b1fbda6c0863b10b98c363
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345076"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Élément personnalisé pour SingleTagSectionHandler

Définit les paramètres d’une section de \<configuration personnalisée qui est <xref:System.Configuration.SingleTagSectionHandler> définie par une section> élément et utilise la classe.

&nbsp; &nbsp; [** \<section**](configuration-element.md) *>Name \<>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Attributs

Les attributs et les valeurs d’attribut sont définis par l’utilisateur.

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes 

La ** \<sectionName>** élément est un élément personnalisé défini par une [** \<section>**](section-element.md) tag dans les [** \<configSections>**](configsections-element-for-configuration.md) élément. Le système de <xref:System.Collections.IDictionary> configuration renvoie un objet lorsque vous appelez <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant déclare un élément personnalisé appelé <xref:System.Configuration.SingleTagSectionHandler> ** \<sampleSection>** qui contient des paramètres lus par la classe :

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](index.md)
