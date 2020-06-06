---
title: <Directives>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84202384"
---
# <a name="directives-element-net-native"></a>\<Directives>, Élément (.NET Native)
Élément racine dans chaque fichier de directives Runtime pour .NET Native.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xmlns`|Espace de noms XML. Sa valeur est toujours `http://schemas.microsoft.com/netfx/2013/01/metadata` .|  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.|  
|[\<Library>](library-element-net-native.md)|Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.|  
  
## <a name="remarks"></a>Remarques  
 Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.  
  
 L' `<Directives>` élément peut contenir zéro ou un [\<Application>](application-element-net-native.md) élément, et zéro, un ou plusieurs [\<Library>](library-element-net-native.md) éléments.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
