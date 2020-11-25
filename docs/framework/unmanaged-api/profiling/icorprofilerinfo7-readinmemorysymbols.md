---
title: 'ICorProfilerInfo7 :: ReadInMemorySymbols'
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
ms.openlocfilehash: 6917900b7494550992dfa82f45ed0140f95e68cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733618"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7 :: ReadInMemorySymbols

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
 à Pointeur vers la mémoire tampon dans laquelle les données seront copiées. La mémoire tampon doit avoir un `countSymbolBytes` espace disponible.  
  
 `countSymbolBytes`  
 dans Nombre d’octets à copier.  
  
 `pCountSymbolBytesRead`  
 à Lorsque la méthode est retournée, contient le nombre réel d’octets lus.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK`, si un nombre d’octets différent de zéro a été lu.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`Si le module a été créé à l’aide de <xref:System.Reflection.Emit> .  
  
## <a name="remarks"></a>Remarques  

 La `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` des données en commençant à      `symbolsReadOffset` l’offset dans le flux en mémoire. Les données sont copiées vers `pSymbolBytes` , ce qui est supposé avoir un `countSymbolBytes` espace disponible.     `pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieur à `countSymbolBytes` si la fin du flux est atteinte.  
  
> [!NOTE]
> L’implémentation actuelle ne prend pas en charge la réflexion. Emit. Si le module a été créé à l’aide de Reflection. Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)
