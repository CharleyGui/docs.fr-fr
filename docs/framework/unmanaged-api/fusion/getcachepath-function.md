---
title: GetCachePath, fonction
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724466"
---
# <a name="getcachepath-function"></a>GetCachePath, fonction

Obtient le chemin d’accès à l’assembly mis en cache, à l’aide des indicateurs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwCacheFlags`  
 dans Valeur [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) qui indique la source de l’assembly mis en cache.  
  
 `pwzCachePath`  
 à Pointeur retourné vers le chemin d’accès.  
  
 `pcchPath`  
 [in, out] La longueur maximale demandée de `pwzCachePath` , et au retour, la longueur réelle de `pwzCachePath` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ASM_CACHE_FLAGS, énumération](asm-cache-flags-enumeration.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
