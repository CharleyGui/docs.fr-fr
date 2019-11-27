---
title: ISymUnmanagedReader2::GetSymAttributePreRemap, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 4009f8988c90ed090c0cc3d86164af347055722f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446423"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap, méthode
Obtient un attribut personnalisé en fonction de son nom. Contrairement aux attributs personnalisés des métadonnées, ces attributs sont conservés dans le magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `parent`  
 dans Jeton de métadonnées du parent.  
  
 `name`  
 dans Pointeur vers un `WCHAR` qui contient le nom.  
  
 `cBuffer`  
 dans `ULONG32` qui indique la taille du tableau de `buffer`.  
  
 `pcBuffer`  
 à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les octets d’attributs.  
  
 `buffer`  
 à Pointeur vers la mémoire tampon qui reçoit les octets d’attributs.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
