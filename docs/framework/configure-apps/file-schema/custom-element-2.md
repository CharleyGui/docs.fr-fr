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
ms.openlocfilehash: 8636050b2618d1b2c2da0c08c756b0ed221c7f6f
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300760"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler

Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)\
&nbsp;&nbsp; **\<sectionName>**

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<Ajouter >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>  | Ajoute des paramètres d’application personnalisés. |
| [ **\<Supprimer >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> | Supprime un paramètre défini précédemment. |
| [ **\<Désactivez >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> | Efface tous les paramètres déjà définis dans une section. |

## <a name="remarks"></a>Notes

Le  **\<sectionName >** est un élément personnalisé défini par un  **\<section >** balise dans le  **\<configSections >** élément.

Le tableau suivant présente que le type d’objet de la méthode ConfigurationSettings.GetConfig retourne pour chaque gestionnaire de section de configuration :

| Gestionnaire de section de configuration                        | Type de retour                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer les sections qui utilisent le <xref:System.Configuration.DictionarySectionHandler> et <xref:System.Configuration.NameValueSectionHandler> classes.

Le premier élément personnalisé est  **\<dictionarySample >** , qui contient les paramètres lus par le <xref:System.Configuration.DictionarySectionHandler> classe dans le `System.dll` assembly. Le deuxième élément personnalisé est  **\<mySection >** , qui contient les paramètres lus par le <xref:System.Configuration.NameValueSectionHandler> classe dans le `System.dll` assembly.

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

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
