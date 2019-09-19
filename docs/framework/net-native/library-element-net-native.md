---
title: <Library>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049644"
---
# <a name="library-element-net-native"></a>\<Élément > de la bibliothèque (.NET Native)
Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.  
  
 \<Directives>, élément  
\<Library>, élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Attribut requis. Spécifie le nom d'un assembly. Les éléments enfants de cet élément `<Library>` définissent la stratégie de réflexion runtime pour les types et membres de type se trouvant dans cet assembly.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*nom_assembly*|Nom simple de l’assembly, sans son extension de fichier. Cet attribut correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Par exemple, le nom d’un assembly nommé Extensions.dll est « Extensions ». Consultez la section Notes pour connaître une forme particulière de *nom_assembly* qui prend en charge l’inclusion conditionnelle de métadonnées à partir de l’assembly.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[\<Namespace>](namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit. Par exemple, vous pouvez utiliser un élément [\<TypeInstantiation>](typeinstantiation-element-net-native.md) afin de définir une stratégie pour un type `List<String>`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## <a name="remarks"></a>Notes  
 L’élément [\<Directives>](directives-element-net-native.md) peut contenir zéro, un ou plusieurs éléments `<Library>`.  
  
 L'élément `<Library>` sert de conteneur pour la définition des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution ; cet élément n'exprime pas la stratégie. Au moment de la compilation, les outils du compilateur recherchent uniquement dans la bibliothèque désignée par l'élément `<Library>` les éléments de programme identifiés par ses éléments enfants. En revanche, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du Framework .NET, les éléments de programme identifiés par les éléments enfants de l’élément [\<Application>](application-element-net-native.md).  
  
 Les directives `<Library>` peuvent être utilisées de manière conditionnelle. Si le nom de l' `<Library>` élément commence et se termine par un\*astérisque () `<Library>` , la directive a un effet uniquement si l’assembly spécifié entre les astérisques est référencé par l’application. Par exemple, la directive Runtime suivante s’applique uniquement si l’assembly Utilities. dll est référencé par l’application.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Voir aussi

- [\<Élément d' > d’application](application-element-net-native.md)
- [\<Directive, élément >](directives-element-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
