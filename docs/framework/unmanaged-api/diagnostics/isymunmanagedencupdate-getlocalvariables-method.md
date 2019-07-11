---
title: ISymUnmanagedENCUpdate::GetLocalVariables, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48e359f8ed4d52de1cff7ca46a523f4eb80ec4c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776905"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables, méthode
Obtient les variables locales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mdMethodToken`  
 [in] Le jeton de métadonnées de la méthode.  
  
 `cLocals`  
 [in] Un `ULONG` qui indique la taille de la `rgLocals` paramètre.  
  
 `rgLocals`  
 [out] Le tableau retourné [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.  
  
 `pceltFetched`  
 [out] Un pointeur vers un `ULONG` qui reçoit la taille de la `rgLocals` tampon nécessaire pour contenir les variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedENCUpdate, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
