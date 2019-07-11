---
title: ICorDebugThread2::GetActiveFunctions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf3998d7430348cb71af8e7dd75cf2203d380ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769034"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions, méthode
Obtient des informations sur la fonction active dans chacun des frames de ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cFunctions`  
 [in] Taille du tableau `pFunctions`.  
  
 `pcFunctions`  
 [out] Un pointeur vers le nombre d’objets retournés dans le `pFunctions` tableau. Le nombre d’objets retourné sera égal au nombre de frames managés sur la pile.  
  
 `pFunctions`  
 [in, out] Tableau d’objets COR_ACTIVE_FUNCTION, chacun d’eux contient des informations sur les fonctions actives dans les frames de ce thread.  
  
 Le premier élément sera utilisé pour le frame terminal et ainsi de suite jusqu’à la racine de la pile.  
  
## <a name="remarks"></a>Notes  
 Si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne uniquement le nombre de fonctions qui se trouvent sur la pile. Autrement dit, si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne une valeur uniquement dans `pcFunctions`.  
  
 Le `GetActiveFunctions` méthode constitue une optimisation sur obtenir les mêmes informations à partir des frames dans une trace de pile et inclut uniquement les frames qui auraient eu un objet ICorDebugILFrame pour eux dans la trace de pile complète.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
