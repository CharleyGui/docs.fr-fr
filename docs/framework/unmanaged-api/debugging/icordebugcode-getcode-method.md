---
title: ICorDebugCode::GetCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179000"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode, méthode
Obtient tout le code pour la fonction spécifiée, formaté pour démontage. Cette méthode a été dépréciée dans la version cadre .NET 2.0. Utilisez [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `startOffset`  
 [dans] Le décalage du début de la fonction.  
  
 `endOffset`  
 [dans] Le décalage de la fin de la fonction.  
  
 `cBufferAlloc`  
 [dans] La taille `buffer` du tableau dans lequel le code sera retourné.  
  
 `buffer`  
 [out] Le tableau dans lequel le code sera retourné.  
  
 `pcBufferSize`  
 [out] Le nombre d’octets est revenu.  
  
## <a name="remarks"></a>Notes   
 Si le code de la fonction a été divisé en plusieurs morceaux, ils sont concatenated dans l’ordre d’augmenter la compensation indigène. Les limites de l’instruction ne sont pas vérifiées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions cadre .NET:** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi

- [GetCodeChunks, méthode](icordebugcode2-getcodechunks-method.md)
