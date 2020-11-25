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
ms.openlocfilehash: 5afc91d1dc6d02f052e860787ebf0858a2f5d12d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730043"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope, méthode

Ouvre une nouvelle portée lexicale dans la méthode actuelle. La portée devient la nouvelle portée actuelle et fait l’objet d’un push dans une pile d’étendues. Les étendues doivent former une hiérarchie. Les frères ne sont pas autorisés à se chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  

 `startOffset`  
 dans Offset de la première instruction dans la portée lexicale, en octets, à partir du début de la méthode.  
  
 `pRetVal`  
 à Pointeur vers un `ULONG32` qui reçoit l’identificateur de portée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Remarques  

 `ISymUnmanagedWriter::OpenScope` retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter :: SetScopeRange,](isymunmanagedwriter-setscoperange-method.md) pour définir le décalage de début et de fin d’une portée ultérieurement. Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter :: CloseScope,](isymunmanagedwriter-closescope-method.md) sont ignorés. Les identificateurs d’étendue sont valides uniquement dans la méthode actuelle.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
