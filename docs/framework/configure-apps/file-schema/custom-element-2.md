---
title: Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215479"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler

Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp; **\<** de la >

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<ajouter des >** ](add-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>  | Ajoute des paramètres d’application personnalisés. |
| [ **\<supprimer >** ](remove-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> | Supprime un paramètre défini précédemment. |
| [ **\<> Clear**](clear-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> | Efface tous les paramètres précédemment définis dans une section. |

## <a name="remarks"></a>Notes

L’élément\<de l’élément de **>** est un élément personnalisé défini par un **\<section >** balise dans l’élément **\<configSections >** .

Le tableau suivant indique le type d’objet retourné par la méthode ConfigurationSettings. GetConfig pour chaque gestionnaire de section de configuration :

| Gestionnaire de section de configuration                        | Type de retour                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer des sections qui utilisent les classes <xref:System.Configuration.DictionarySectionHandler> et <xref:System.Configuration.NameValueSectionHandler>.

Le premier élément personnalisé est **\<dictionarySample >** , qui contient les paramètres lus par la classe <xref:System.Configuration.DictionarySectionHandler> de l’assembly `System.dll`. Le deuxième élément personnalisé est **\<mySection >** , qui contient les paramètres lus par la classe <xref:System.Configuration.NameValueSectionHandler> de l’assembly `System.dll`.

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

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
