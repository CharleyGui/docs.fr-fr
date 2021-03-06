---
title: ISymUnmanagedMethod::GetSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 38763e687c66dcb038a874c9c17cb0d67e547816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699350"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints, méthode

Obtient tous les points de séquence de cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cPoints`  
 dans `ULONG32` Qui reçoit la taille des tableaux,,,, `offsets` `documents` `lines` `columns` `endLines` et `endColumns` .  
  
 `pcPoints`  
 à Pointeur vers `ULONG32` qui reçoit la longueur de la mémoire tampon requise pour contenir les points de séquence.  
  
 `offsets`  
 dans Tableau dans lequel stocker les offsets MSIL (Microsoft Intermediate Language) à partir du début de la méthode pour les points de séquence.  
  
 `documents`  
 dans Tableau dans lequel stocker les documents dans lesquels se trouvent les points de séquence.  
  
 `lines`  
 dans Tableau dans lequel stocker les lignes des documents où se trouvent les points de séquence.  
  
 `columns`  
 dans Tableau dans lequel stocker les colonnes des documents où se trouvent les points de séquence.  
  
 `endLines`  
 dans Tableau de lignes des documents où se terminent les points de séquence.  
  
 `endColumns`  
 dans Tableau de colonnes dans les documents où se terminent les points de séquence.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedMethod, interface](isymunmanagedmethod-interface.md)
