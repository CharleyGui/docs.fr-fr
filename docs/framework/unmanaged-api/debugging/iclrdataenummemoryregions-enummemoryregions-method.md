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
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785636"
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
  
## <a name="parameters"></a>Parameters  
 `callback`  
 dans Pointeur vers une instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) qui est appelée par cette méthode pour chaque région de mémoire qui est énumérée pour notifier le débogueur du résultat.  
  
 L’énumération des régions de la mémoire se poursuit même si le rappel indique un échec.  
  
 `miniDumpFlags`  
 dans Non utilisé.  
  
 `clrFlags`  
 dans Valeur de l’énumération [CLRDataEnumMemoryFlags,](clrdataenummemoryflags-enumeration.md) qui spécifie les régions de mémoire à énumérer.  
  
## <a name="remarks"></a>Notes  
 Cette méthode utilise l’instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) spécifiée pour notifier les résultats à l’appelant.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataEnumMemoryRegions, interface](iclrdataenummemoryregions-interface.md)
