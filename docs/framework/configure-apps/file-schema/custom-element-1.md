---
title: Élément personnalisé pour SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927498"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Élément personnalisé pour SingleTagSectionHandler

Définit des paramètres dans une section de configuration personnalisée définie par une \<section > élément et utilise la <xref:System.Configuration.SingleTagSectionHandler> classe.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Attributs

Les attributs et les valeurs d’attribut sont définis par l’utilisateur.

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

L'  **\<** élément de >y est un élément personnalisé défini par [ **\<** ](section-element.md) une balise de > de section dans l' [ **\<élément configSections >** ](configsections-element-for-configuration.md) . Le système de configuration retourne <xref:System.Collections.IDictionary> un objet lorsque vous <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>appelez.

## <a name="example"></a>Exemple

L’exemple suivant déclare un élément personnalisé appelé  **\<sampleSection >** qui contient les paramètres lus par la <xref:System.Configuration.SingleTagSectionHandler> classe:

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

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
