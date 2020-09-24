---
title: Élément <clear> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: d65712f091c5fb9212167b4759c70db7e5d744c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149411"
---
# <a name="clear-element-for-namedcaches"></a>\<clear>, élément de \<namedCaches>

Efface toutes les `namedCache` entrées de la `namedCaches` collection pour un cache mémoire.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Type  

 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 `None`  
  
### <a name="child-elements"></a>Éléments enfants  

 `None`  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.|  
  
## <a name="remarks"></a>Notes  

 L' `clear` élément efface toutes les `namedCache` entrées de la collection de caches nommée pour un cache mémoire. Vous pouvez utiliser l' `clear` élément avant d’utiliser l' `add` élément pour ajouter une nouvelle entrée de cache nommée afin d’être certain qu’il n’existe aucun autre cache nommé dans la collection.  
  
## <a name="see-also"></a>Voir aussi

- [\<namedCaches> , Élément (paramètres de cache)](namedcaches-element-cache-settings.md)
