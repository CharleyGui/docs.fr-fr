---
title: élément <add> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e7d68530ae1f0666fc4940ffe7605c3bf8dfe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119615"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<ajouter un élément > pour NameValueSectionHandler et DictionarySectionHandler

Ajoute des paramètres d’application personnalisés. Chaque **\<ajouter >** balise contient une paire clé/valeur.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la  >.  
&nbsp;&nbsp;&nbsp;&nbsp; **\<ajouter des >**

## <a name="syntax"></a>Syntaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Attributs

| Attribut | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom du paramètre. |
| **valeur** | Attribut requis.<br><br>Spécifie la valeur du paramètre. |

## <a name="parent-element"></a>Élément parent

| Élément | Description |
| ------- | ------------|
| [ **\<** de la > Appartient](custom-element-2.md) | Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Éléments enfants

aucune.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration personnalisée et utiliser l’élément **\<ajouter >** pour placer des paramètres dans la section :

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
