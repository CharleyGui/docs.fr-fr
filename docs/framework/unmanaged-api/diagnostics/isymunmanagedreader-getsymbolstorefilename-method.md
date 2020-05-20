---
title: ISymUnmanagedReader::GetSymbolStoreFileName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: 6ffab3b2f81680404f870cfd63ae5125173a346c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615512"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a>ISymUnmanagedReader::GetSymbolStoreFileName, méthode
Fournit le nom de fichier sur disque du magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 dans Taille de la `szName` mémoire tampon.  
  
 `pcchName`  
 à Pointeur vers la variable qui reçoit la longueur du nom retourné dans `szName` , y compris l’arrêt null.  
  
 `szName`  
 à Pointeur vers la variable qui reçoit le nom de fichier du magasin de symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)
