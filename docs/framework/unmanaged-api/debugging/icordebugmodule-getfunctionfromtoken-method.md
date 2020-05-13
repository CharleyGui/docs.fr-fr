---
title: ICorDebugModule::GetFunctionFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212579"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken, méthode
Obtient la fonction spécifiée par le jeton de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `methodDef`  
 dans `mdMethodDef`Jeton de métadonnées qui fait référence aux métadonnées de la fonction.  
  
 `ppFunction`  
 à Pointeur vers l’adresse d’un objet d’interface ICorDebugFunction qui représente la fonction.  
  
## <a name="remarks"></a>Remarks  
 La `GetFunctionFromToken` méthode retourne un CORDBG_E_FUNCTION_NOT_IL HRESULT si la valeur passée `methodDef` ne fait pas référence à une méthode MSIL (Microsoft Intermediate Language).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
