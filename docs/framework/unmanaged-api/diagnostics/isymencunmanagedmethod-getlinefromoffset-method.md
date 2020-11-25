---
title: ISymENCUnmanagedMethod::GetLineFromOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707358"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset, méthode

Obtient les informations de ligne associées à un offset. Si le paramètre de décalage ( `dwOffset` ) n’est pas un point de séquence, cette méthode obtient les informations de ligne associées au décalage précédent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwOffset`  
 dans `ULONG32` Qui contient l’offset.  
  
 `pline`  
 à Pointeur vers un `ULONG32` qui reçoit la ligne.  
  
 `pcolumn`  
 à Pointeur vers un `ULONG32` qui reçoit la colonne.  
  
 `pendLine`  
 à Pointeur vers un `ULONG32` qui reçoit la ligne de fin.  
  
 `pendColumn`  
 à Pointeur vers un `ULONG32` qui reçoit la colonne de fin.  
  
 `pdwStartOffset`  
 à Pointeur vers un `ULONG32` qui reçoit le point de séquence associé.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymENCUnmanagedMethod, interface](isymencunmanagedmethod-interface.md)
