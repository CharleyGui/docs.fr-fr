---
title: <Library>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128366"
---
# <a name="library-element-net-native"></a>\<Library>, Élément (.NET Native)
Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.  
  
 Élément \<Directives>  
Élément \<Library>  
  
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
|*assembly_name*|Nom simple de l’assembly, sans son extension de fichier. Cet attribut correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Par exemple, le nom d’un assembly nommé Extensions.dll est « Extensions ». Consultez la section Notes pour connaître une forme particulière de *nom_assembly* qui prend en charge l’inclusion conditionnelle de métadonnées à partir de l’assembly.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[\<Namespace>](namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit. Par exemple, un [\<TypeInstantiation>](typeinstantiation-element-net-native.md) élément peut être utilisé pour définir la stratégie d’un `List<String>` type.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## <a name="remarks"></a>Remarques  
 L' [\<Directives>](directives-element-net-native.md) élément peut contenir zéro, un ou plusieurs `<Library>` éléments.  
  
 L'élément `<Library>` sert de conteneur pour la définition des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution ; cet élément n'exprime pas la stratégie. Au moment de la compilation, les outils du compilateur recherchent uniquement dans la bibliothèque désignée par l'élément `<Library>` les éléments de programme identifiés par ses éléments enfants. En revanche, les outils du compilateur recherchent dans toutes les bibliothèques, including.NET Framework Core Libraries, les éléments de programme identifiés par les éléments enfants de l' [\<Application>](application-element-net-native.md) élément.  
  
 Les directives `<Library>` peuvent être utilisées de manière conditionnelle. Si le nom de l' `<Library>` élément commence et se termine par un astérisque ( \* ), la `<Library>` directive a un effet uniquement si l’assembly spécifié entre les astérisques est référencé par l’application. Par exemple, la directive Runtime suivante s’applique uniquement si l’assembly Utilities. dll est référencé par l’application.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Voir aussi

- [\<Application>Appartient](application-element-net-native.md)
- [\<Directives>Appartient](directives-element-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
