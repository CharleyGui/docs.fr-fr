---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 857410187edf1c712865626a3327dd4c92cc211f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441927"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset, méthode
Obtient le nom de fichier pour la ligne associée à un offset.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwOffset`  
 dans `ULONG32`Qui contient l’offset.  
  
 `cchName`  
 dans `ULONG32`Qui indique la taille de la `szName` mémoire tampon.  
  
 `pcchName`  
 à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon qui doit contenir les noms de fichiers.  
  
 `szName`  
 à Mémoire tampon qui contient les noms de fichiers.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymENCUnmanagedMethod, interface](isymencunmanagedmethod-interface.md)
