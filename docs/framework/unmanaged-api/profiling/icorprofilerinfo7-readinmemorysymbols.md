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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868341"
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
  
## <a name="parameters"></a>Parameters  
 `moduleId`  
 dans Identificateur du module contenant le flux en mémoire.  
  
 `symbolsReadOffset`  
 dans Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.  
  
 `pSymbolBytes`  
 à Pointeur vers la mémoire tampon dans laquelle les données seront copiées. La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.  
  
 `countSymbolBytes`  
 dans Nombre d’octets à copier.  
  
 `pCountSymbolBytesRead`  
 à Lorsque la méthode est retournée, contient le nombre réel d’octets lus.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`, si un nombre d’octets différent de zéro a été lu.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Notes  
 La méthode `ReadInMemorySymbols` tente de lire `countSymbolBytes` de données à partir du décalage `symbolsReadOffset` dans le flux en mémoire. Les données sont copiées vers `pSymbolBytes`, qui est censée avoir `countSymbolBytes` d’espace disponible.     `pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieur à `countSymbolBytes` si la fin du flux est atteinte.  
  
> [!NOTE]
> L’implémentation actuelle ne prend pas en charge la réflexion. Emit. Si le module a été créé à l’aide de Reflection. Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)
