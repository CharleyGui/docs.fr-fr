---
title: ISymUnmanagedENCUpdate::UpdateMethodLines, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 99499b8717f219616b6b368e6393b4b7ca0a79d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699584"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines, méthode

Autorise la mise à jour des informations de ligne pour une méthode qui n’a pas été recompilée, mais dont les lignes ont été déplacées indépendamment. Un Delta est autorisé pour chaque instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>Paramètres  

 `mdMethodToken`  
 dans Métadonnées du jeton de la méthode.  
  
 `pDeltas`  
 dans Tableau de `INT32` valeurs qui indique des deltas pour chaque point de séquence dans la méthode.  
  
 `cDeltas`  
 dans `ULONG` Contenant la taille du `pDeltas` paramètre.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedENCUpdate, interface](isymunmanagedencupdate-interface.md)
