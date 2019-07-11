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
ms.openlocfilehash: cd337ca6d7b03ad22f178c9c7084cfa2585da73c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782750"
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
 [in] L’ID de l’objet.  
  
 `pcSize`  
 [out] Pointeur vers la taille de l’objet, en octets.  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
>  Cette méthode est obsolète. Renvoie la COR_E_OVERFLOW objets supérieur à 4 Go sur les plateformes 64 bits. Utilisez le [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) méthode à la place.  
  
 Différents objets des mêmes types ont souvent la même taille. Toutefois, certains types, tels que des tableaux ou des chaînes, peuvent avoir une taille différente pour chaque objet.  
  
 La taille retournée par la `GetObjectSize` méthode n’inclut pas de marge intérieure alignement susceptibles d’apparaître une fois que l’objet est sur le tas de garbage collection. Si vous utilisez le `GetObjectSize` méthode pour passer d’un objet à l’objet sur le tas de garbage collection, ajoutez alignement remplissage manuellement, en fonction des besoins.  
  
- Sur Windows 32 bits, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 et COR_PRF_GC_GEN_2 utilisent alignement de 4 octets, et COR_PRF_GC_LARGE_OBJECT_HEAP utilise l’alignement de 8 octets.  
  
- Sur Windows 64 bits, l’alignement est toujours de 8 octets.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
