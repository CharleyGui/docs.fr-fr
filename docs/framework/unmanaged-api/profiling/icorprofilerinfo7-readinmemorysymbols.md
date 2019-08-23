---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955368"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Lit les octets d’un flux de symboles en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleId`  
 dans Identificateur du module contenant le flux en mémoire.  
  
 `symbolsReadOffset`  
 dans Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.  
  
 `pSymbolBytes`  
 à Pointeur vers la mémoire tampon dans laquelle les données seront copiées. La mémoire tampon doit `countSymbolBytes` avoir un espace disponible.  
  
 `countSymbolBytes`  
 dans Nombre d’octets à copier.  
  
 `pCountSymbolBytesRead`  
 à Lorsque la méthode est retournée, contient le nombre réel d’octets lus.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`, si un nombre d’octets différent de zéro a été lu.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`Si le module a été créé à <xref:System.Reflection.Emit>l’aide de.  
  
## <a name="remarks"></a>Notes  
 La `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` des données en commençant à `symbolsReadOffset` l’offset dans le flux en mémoire. Les données sont copiées `pSymbolBytes`vers, ce qui est supposé `countSymbolBytes` avoir un espace disponible.     `pCountSymbolsBytesRead`contient le nombre réel d’octets lus, qui peut être inférieur à `countSymbolBytes` si la fin du flux est atteinte.  
  
> [!NOTE]
> L’implémentation actuelle ne prend pas en charge la réflexion. Emit. Si le module a été créé à l’aide de Reflection. Emit `CORPROF_E_MODULE_IS_DYNAMIC`, la méthode retourne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
