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
ms.openlocfilehash: 2a878ccf94fb4f6d67daa3a4dd42fcf98faf34a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748641"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Lit les octets à partir d’un flux de symbole d’en mémoire.  
  
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
 [in] L’identificateur du module qui contient le flux en mémoire.  
  
 `symbolsReadOffset`  
 [in] Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.  
  
 `pSymbolBytes`  
 [out] Pointeur vers la mémoire tampon à laquelle les données seront copiées. La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.  
  
 `countSymbolBytes`  
 [in] Le nombre d’octets à copier.  
  
 `pCountSymbolBytesRead`  
 [out] Lorsque la méthode est retournée, contient le nombre réel d’octets lus.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`, si un nombre d’octets lus.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Notes  
 Le `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` de données en commençant au décalage `symbolsReadOffset` dans le flux en mémoire. Les données sont copiées vers `pSymbolBytes`, qui est censé avoir `countSymbolBytes` d’espace disponible.     `pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieure à `countSymbolBytes` si la fin du flux est atteinte.  
  
> [!NOTE]
>  L’implémentation actuelle ne prend pas en charge de Reflection.Emit. Si le module a été créé à l’aide de Reflection.Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
