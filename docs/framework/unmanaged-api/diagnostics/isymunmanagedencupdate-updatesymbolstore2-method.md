---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: c68cf632b789a523b19cc78d8d919c2278b1befa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699571"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2, méthode

Permet à un compilateur d’omettre les fonctions qui n’ont pas été modifiées à partir du flux de la base de données du programme (PDB), à condition que les informations de ligne répondent à la configuration requise. Les informations de ligne correctes peuvent être déterminées par les anciennes informations de ligne PDB et un Delta pour toutes les lignes de la fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pIStream`  
 dans Pointeur vers un [IStream](/windows/desktop/api/objidl/nn-objidl-istream) qui contient les informations de ligne.  
  
 `pDeltaLines`  
 dans Pointeur vers une structure [SYMLINEDELTA](symlinedelta-structure.md) qui contient les lignes qui ont changé.  
  
 `cDeltaLines`  
 dans `ULONG` Qui représente le nombre de lignes qui ont changé.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedENCUpdate, interface](isymunmanagedencupdate-interface.md)
