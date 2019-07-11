---
title: ICorDebugThread2::GetConnectionID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768971"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID, méthode
Obtient l’identificateur de connexion pour cet objet ICorDebugThread2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwConnectionId`  
 [out] Un `CONNID` qui représente l’identificateur de connexion.  
  
## <a name="remarks"></a>Notes  
 Le `GetConnectionID` méthode retourne la valeur zéro dans le `pdwConnectionId` paramètre, si ce thread ne fait pas partie d’une connexion.  
  
 Si ce thread est connecté à une instance de Microsoft SQL Server 2005 Analysis Services (SSAS), le `CONNID` est mappé à un identificateur de processus serveur (SPID).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
