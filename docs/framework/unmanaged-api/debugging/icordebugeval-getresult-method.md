---
title: ICorDebugEval::GetResult, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 86c017f581c7b980b8b0cb8bd7bdc1b0aa439afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705819"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult, méthode

Obtient les résultats de cette évaluation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppResult`  
 à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente les résultats de cette évaluation, si l’évaluation se termine normalement.  
  
## <a name="remarks"></a>Remarques  

 La `GetResult` méthode est valide uniquement une fois l’évaluation terminée.  
  
 Si l’évaluation se termine normalement, `ppResult` spécifie les résultats. Si elle se termine avec une exception, le résultat est l’exception levée. Si l’évaluation s’est produite pour un nouvel objet, le résultat est la référence au nouvel objet.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
