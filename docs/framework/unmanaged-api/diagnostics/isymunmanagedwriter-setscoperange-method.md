---
title: ISymUnmanagedWriter::SetScopeRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: b57bb549278f62cdce6ed5deaaa62f154ec919b5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609363"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange, méthode
Définit la plage d'offsets pour la portée lexicale spécifiée. La portée devient la nouvelle portée actuelle et fait l’objet d’un push dans une pile d’étendues. Les étendues doivent former une hiérarchie. Les frères ne sont pas autorisés à se chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
 `scopeId`  
 dans Identificateur de portée de l’étendue.  
  
 `startOffset`  
 dans Offset, en octets, de la première instruction dans la portée lexicale à partir du début de la méthode.  
  
 `endOffset`  
 dans Offset, en octets, de la dernière instruction dans la portée lexicale à partir du début de la méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Notes  
 [ISymUnmanagedWriter :: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec `ISymUnmanagedWriter::SetScopeRange` pour définir les offsets de début et de fin d’une portée ultérieurement. Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter :: CloseScope,](isymunmanagedwriter-closescope-method.md) sont ignorés. Les identificateurs de portée sont valides uniquement dans la méthode actuelle.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
