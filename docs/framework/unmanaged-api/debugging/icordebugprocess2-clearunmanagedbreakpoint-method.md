---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: a713fd006f1e9ad8fe7109651c2cda5025da3566
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673941"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode

Supprime un point d’arrêt défini précédemment à l’adresse donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `address`  
 dans `CORDB_ADDRESS` Valeur qui spécifie l’adresse à laquelle le point d’arrêt a été défini.  
  
## <a name="remarks"></a>Remarques  

 Le point d’arrêt spécifié aurait été précédemment défini par un appel antérieur à [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 La `ClearUnmanagedBreakpoint` méthode peut être appelée pendant l’exécution du processus en cours de débogage.  
  
 La `ClearUnmanagedBreakpoint` méthode retourne un code d’échec si le débogueur est attaché en mode managé uniquement ou si aucun point d’arrêt n’existe à l’adresse spécifiée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
