---
title: ISymUnmanagedScope::GetLocalCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 3b5dbe875b47f48c24c5e955abddb2c6f778bcdd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446337"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a>ISymUnmanagedScope::GetLocalCount, méthode
Obtient le nombre de variables locales définies dans cette portée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Pointeur vers un `ULONG32` qui reçoit le nombre de variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedScope, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
