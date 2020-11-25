---
title: ICorDebugClass2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717823"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus, méthode

Pour chaque méthode de la classe, définit une valeur qui indique si la méthode est du code défini par l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `bIsJustMyCode`  
 dans Affectez `true` la valeur pour indiquer que la méthode est du code défini par l’utilisateur ; sinon, affectez à la valeur `false` .  
  
## <a name="remarks"></a>Remarques  

 Une exécution pas à pas juste-à-pas-code (uniquement mon code) ignore le code non défini par l’utilisateur. Le code défini par l’utilisateur doit être un sous-ensemble du code pouvant être débogué.  
  
 `SetJMCStatus` retourne une valeur HRESULT de S_FALSE si elle ne parvient pas à définir la valeur d’une méthode, même si elle définit correctement la valeur pour toutes les autres méthodes.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
