---
title: ISymUnmanagedNamespace::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 43f32ac85bebc12d0a9253205aae3f1de0dc9e5b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433965"
---
# <a name="isymunmanagednamespacegetname-method"></a>ISymUnmanagedNamespace::GetName, méthode
Obtient le nom de cet espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 dans `ULONG32` qui indique la taille de la mémoire tampon de `szName`.  
  
 `pcchName`  
 à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom de l’espace de noms, y compris la terminaison NULL.  
  
 `szName`  
 à Pointeur vers une mémoire tampon qui contient le nom de l’espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedNamespace, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
