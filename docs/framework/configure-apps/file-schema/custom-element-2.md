---
title: Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921040"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler

Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp; **\<sectionName>**

## <a name="attributes"></a>Attributs

Aucun

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| Ajouter > pour et [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler>  | Ajoute des paramètres d’application personnalisés. |
| supprimer > pour et [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler> | Supprime un paramètre défini précédemment. |
| désactivez <xref:System.Configuration.NameValueSectionHandler> > pour et [ **\<** ](clear-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler> | Efface tous les paramètres précédemment définis dans une section. |

## <a name="remarks"></a>Notes

L'  **\<** élément de >y est un élément personnalisé défini par  **\<** une balise de > de section dans l'  **\<élément configSections >** .

Le tableau suivant indique le type d’objet retourné par la méthode ConfigurationSettings. GetConfig pour chaque gestionnaire de section de configuration:

| Gestionnaire de section de configuration                        | Type de retour                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Exemples

L’exemple suivant montre comment déclarer des sections qui utilisent les <xref:System.Configuration.DictionarySectionHandler> classes <xref:System.Configuration.NameValueSectionHandler> et.

Le premier élément personnalisé est  **\<dictionarySample >** , qui contient les paramètres lus par <xref:System.Configuration.DictionarySectionHandler> la classe dans `System.dll` l’assembly. Le deuxième élément personnalisé est  **\<mySection >** , qui contient les paramètres lus par <xref:System.Configuration.NameValueSectionHandler> la classe dans `System.dll` l’assembly.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
