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
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709646"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus, méthode

Affecte la valeur spécifiée à l’état Uniquement mon code (uniquement mon code) de toutes les méthodes de toutes les classes de ce ICorDebugModule2, à l’exception de celles du `pTokens` tableau, qu’il affecte à la valeur opposée.  
  
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
 dans Affectez `true` la valeur si le code doit être débogué ; sinon, affectez à la valeur `false` .  
  
 `cTokens`  
 [in] Taille du tableau `pTokens`.  
  
 `pTokens`  
 dans Tableau de `mdToken` valeurs, dont chacune fait référence à une méthode dont l’état uniquement mon code est défini sur ! `bIsJustMycode` .  
  
## <a name="remarks"></a>Remarques  

 L’état uniquement mon code de chaque méthode spécifiée dans le `pTokens` tableau est défini sur le contraire de la `bIsJustMycode` valeur. L’état de toutes les autres méthodes de ce module est défini sur la `bIsJustMycode` valeur.  
  
 La `SetJMCStatus` méthode efface tous les paramètres uniquement mon code précédents de ce module.  
  
 La `SetJMCStatus` méthode retourne un S_OK HRESULT si toutes les fonctions ont été correctement définies. Elle retourne un CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT si certaines fonctions marquées ne `true` peuvent pas être déboguées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
