---
title: ICorDebugChain::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6db1990df2ed6b29d548c147ed40b5bc98254d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745692"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange, méthode
Obtient la plage d’adresses du segment de pile pour cette chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pStart`  
 [out] Un pointeur vers un `CORDB_ADDRESS` valeur qui est l’adresse de départ du segment de pile.  
  
 `pEnd`  
 [out] Un pointeur vers un `CORDB_ADDRESS` valeur qui est l’adresse de fin du segment de pile.  
  
## <a name="remarks"></a>Notes  
 La plage numérique est significative uniquement pour la comparaison des emplacements de frame de pile. Vous ne pouvez pas faire d’hypothèses concernant ce qui est réellement stocké sur la pile.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
