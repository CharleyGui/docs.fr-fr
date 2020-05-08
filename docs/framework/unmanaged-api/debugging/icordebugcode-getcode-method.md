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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893653"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode, méthode
Obtient tout le code pour la fonction spécifiée, mis en forme pour le code machine. Cette méthode est déconseillée dans la version 2,0 de .NET Framework. Utilisez [ICorDebugCode2 :: GetCodeChunks,](icordebugcode2-getcodechunks-method.md) à la place.  
  
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
 dans Offset du début de la fonction.  
  
 `endOffset`  
 dans Offset de la fin de la fonction.  
  
 `cBufferAlloc`  
 dans Taille du `buffer` tableau dans lequel le code sera retourné.  
  
 `buffer`  
 à Tableau dans lequel le code sera retourné.  
  
 `pcBufferSize`  
 à Nombre d’octets retournés.  
  
## <a name="remarks"></a>Notes   
 Si le code de la fonction a été divisé en plusieurs segments, ils sont concaténés par ordre de décalage natif. Les limites d’instruction ne sont pas vérifiées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [GetCodeChunks, méthode](icordebugcode2-getcodechunks-method.md)
