---
title: <add>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921336"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Ajouter > élément pour NameValueSectionHandler et DictionarySectionHandler

Ajoute des paramètres d’application personnalisés. Chaque balise d'  **>Addcontientunepaireclé/valeur\<** .

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>Syntaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Attributs

| Attribut | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom du paramètre. |
| **value** | Attribut requis.<br><br>Spécifie la valeur du paramètre. |

## <a name="parent-element"></a>Élément parent

| Élément | Description |
| ------- | ------------|
| [élément de >y  **\<** ](custom-element-2.md) | Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="example"></a>Exemples

L’exemple suivant montre comment définir une section de configuration personnalisée et utiliser l'  **\<élément Add >** pour placer des paramètres dans la section:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
