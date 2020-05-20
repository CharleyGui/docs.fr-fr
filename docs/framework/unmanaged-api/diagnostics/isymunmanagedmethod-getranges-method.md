---
title: ISymUnmanagedMethod::GetRanges, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: cd5d1f2d59d3e55ba454f23d2e5dd4b1316c0df4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615174"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges, méthode
À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode. Le tableau est un tableau d’entiers et a le format [Start, end, Start, end]. Le nombre de paires de plages est la longueur du tableau divisée par 2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `document`  
 dans Document pour lequel l’offset est demandé.  
  
 `line`  
 dans Ligne du document correspondant aux plages.  
  
 `column`  
 dans Colonne du document correspondant aux plages.  
  
 `cRanges`  
 [in] Taille du tableau `ranges`.  
  
 `pcRanges`  
 à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les plages.  
  
 `ranges`  
 à Pointeur vers la mémoire tampon qui reçoit les plages.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedMethod, interface](isymunmanagedmethod-interface.md)
