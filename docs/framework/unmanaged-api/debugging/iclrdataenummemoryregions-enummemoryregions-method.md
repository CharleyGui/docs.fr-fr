---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: 386f975ab0bbbe804fda2bd7567acf24f69e77fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676073"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode

Énumère les zones de mémoire spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `callback`  
 dans Pointeur vers une instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) qui est appelée par cette méthode pour chaque région de mémoire qui est énumérée pour notifier le débogueur du résultat.  
  
 L’énumération des régions de la mémoire se poursuit même si le rappel indique un échec.  
  
 `miniDumpFlags`  
 [in] Non utilisé.  
  
 `clrFlags`  
 dans Valeur de l’énumération [CLRDataEnumMemoryFlags,](clrdataenummemoryflags-enumeration.md) qui spécifie les régions de mémoire à énumérer.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode utilise l’instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) spécifiée pour notifier les résultats à l’appelant.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataEnumMemoryRegions, interface](iclrdataenummemoryregions-interface.md)
