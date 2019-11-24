---
title: ISymUnmanagedMethod::GetSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448879"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints, méthode
Gets all the sequence points within this method.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cPoints`  
 [in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.  
  
 `pcPoints`  
 [out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.  
  
 `offsets`  
 [in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.  
  
 `documents`  
 [in] An array in which to store the documents in which the sequence points are located.  
  
 `lines`  
 [in] An array in which to store the lines in the documents at which the sequence points are located.  
  
 `columns`  
 [in] An array in which to store the columns in the documents at which the sequence points are located.  
  
 `endLines`  
 [in] The array of lines in the documents at which the sequence points end.  
  
 `endColumns`  
 [in] The array of columns in the documents at which the sequence points end.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>spécifications  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
