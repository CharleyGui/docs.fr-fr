---
title: ICorDebugModule2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129472"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus, méthode
Affecte la valeur spécifiée à l’état Uniquement mon code (uniquement mon code) de toutes les méthodes de toutes les classes de ce ICorDebugModule2, à l’exception de celles du tableau `pTokens`, qu’il affecte à la valeur opposée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bIsJustMycode`  
 dans A la valeur `true` si le code doit être débogué ; Sinon, affectez la valeur `false`.  
  
 `cTokens`  
 [in] Taille du tableau `pTokens`.  
  
 `pTokens`  
 dans Tableau de valeurs `mdToken`, dont chacune fait référence à une méthode dont l’état uniquement mon code a la valeur !`bIsJustMycode`.  
  
## <a name="remarks"></a>Notes  
 L’état uniquement mon code de chaque méthode spécifiée dans le tableau de `pTokens` est défini sur le contraire de la valeur `bIsJustMycode`. L’état de toutes les autres méthodes de ce module est défini sur la valeur `bIsJustMycode`.  
  
 La méthode `SetJMCStatus` efface tous les paramètres uniquement mon code précédents de ce module.  
  
 La méthode `SetJMCStatus` retourne un HRESULT S_OK si toutes les fonctions ont été correctement définies. Elle retourne un HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE si certaines fonctions qui sont marquées `true` ne peuvent pas être déboguées.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
