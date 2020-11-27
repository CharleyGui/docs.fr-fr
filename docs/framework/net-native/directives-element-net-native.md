---
title: <Directives> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251098"
---
# <a name="directives-element-net-native"></a>\<Directives> , Élément (.NET Native)

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
  
## <a name="remarks"></a>Notes  

 Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.  
  
 L' `<Directives>` élément peut contenir zéro ou un [\<Application>](application-element-net-native.md) élément, et zéro, un ou plusieurs [\<Library>](library-element-net-native.md) éléments.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
