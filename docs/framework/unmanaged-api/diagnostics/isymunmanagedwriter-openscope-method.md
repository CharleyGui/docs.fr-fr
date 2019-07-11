---
title: ISymUnmanagedWriter::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6d563873045b4b5b427f06f0caa5420d31590b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777210"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope, méthode
Ouvre une nouvelle portée lexicale dans la méthode actuelle. La portée devient la nouvelle portée actuelle et est envoyée à une pile d’étendues. Les portées doivent former une hiérarchie. Frères ne sont pas autorisées à chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `startOffset`  
 [in] Le décalage de la première instruction dans la portée lexicale, en octets, à partir du début de la méthode.  
  
 `pRetVal`  
 [out] Un pointeur vers un `ULONG32` qui reçoit l’identificateur de portée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Notes  
 `ISymUnmanagedWriter::OpenScope` Retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir une étendue de démarrage et de fin de décalage à partir d’une date ultérieure. Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés. Les identificateurs de portée sont valides uniquement dans la méthode actuelle.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
