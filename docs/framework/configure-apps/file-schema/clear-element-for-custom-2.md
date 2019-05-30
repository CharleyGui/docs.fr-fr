---
title: <clear> élément pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: e5ab12150c5200dc346e950541443d5286f739c8
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301249"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Désactivez >, élément pour NameValueSectionHandler et DictionarySectionHandler

Efface tous les paramètres déjà définis dans une section.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ------------|
| [ **\<sectionName>** Element](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes

Vous pouvez utiliser la  **\<Effacer >** élément à supprimer tous les paramètres de votre application qui ont été définies à un niveau supérieur dans la hiérarchie de fichiers de configuration.

## <a name="example"></a>Exemple

Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser le  **\<Effacer >** élément dans un fichier de configuration d’application pour effacer les sections définies précédemment dans le fichier de configuration machine.

Le code du fichier de configuration machine suivant déclare la section  **\<mySection >** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Le code suivant du fichier de configuration de l’application supprime tous les paramètres à partir de  **\<mySection >** . L’application ne peut pas récupérer les paramètres qui ont été déclarées dans le dans le  **\<mySection >** section du fichier de configuration machine.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
