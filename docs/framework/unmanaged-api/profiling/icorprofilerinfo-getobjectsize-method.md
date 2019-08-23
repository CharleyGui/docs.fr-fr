---
title: ICorProfilerInfo::GetObjectSize, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ad2092c902b137df0dfe108743ef4081ca5f04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948111"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize, méthode
Obtient la taille d’un objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Paramètres  
 `objectId`  
 dans ID de l’objet.  
  
 `pcSize`  
 à Pointeur vers la taille de l’objet, en octets.  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> Cette méthode est obsolète. Elle retourne COR_E_OVERFLOW pour les objets supérieurs à 4 Go sur les plateformes 64 bits. Utilisez la méthode [ICorProfilerInfo4:: getobjectsize2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) à la place.  
  
 Les différents objets des mêmes types ont souvent la même taille. Toutefois, certains types, tels que les tableaux ou les chaînes, peuvent avoir une taille différente pour chaque objet.  
  
 La taille retournée par `GetObjectSize` la méthode n’inclut aucun remplissage d’alignement qui peut apparaître après que l’objet se trouve sur le tas garbage collection. Si vous utilisez la `GetObjectSize` méthode pour passer d’un objet à l’objet sur le tas garbage collection, ajoutez manuellement le remplissage de l’alignement, si nécessaire.  
  
- Sur Windows 32 bits, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 et COR_PRF_GC_GEN_2 utilisent l’alignement sur 4 octets, tandis que COR_PRF_GC_LARGE_OBJECT_HEAP utilise l’alignement sur 8 octets.  
  
- Sur Windows 64 bits, l’alignement est toujours de 8 octets.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
