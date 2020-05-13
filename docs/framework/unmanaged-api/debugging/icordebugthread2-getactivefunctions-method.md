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
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377150"
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
 à Pointeur vers le nombre d’objets retournés dans le `pFunctions` tableau. Le nombre d’objets retournés sera égal au nombre de frames managés sur la pile.  
  
 `pFunctions`  
 [in, out] Tableau d’objets COR_ACTIVE_FUNCTION, chacun contenant des informations sur les fonctions actives dans les frames de ce thread.  
  
 Le premier élément sera utilisé pour le frame de feuille, et ainsi de suite jusqu’à la racine de la pile.  
  
## <a name="remarks"></a>Remarks  
 Si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne uniquement le nombre de fonctions qui se trouvent sur la pile. Autrement dit, si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne une valeur uniquement dans `pcFunctions` .  
  
 La `GetActiveFunctions` méthode est conçue comme une optimisation pour obtenir les mêmes informations à partir de frames dans une trace de la pile, et comprend uniquement les frames qui auraient eu un objet ICorDebugILFrame pour eux dans la trace de la pile complète.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
