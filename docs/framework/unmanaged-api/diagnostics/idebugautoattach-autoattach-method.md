---
title: IDebugAutoAttach::AutoAttach, méthode
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e04a447c8562ff797ac98885bded150a3a167136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775801"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach, méthode
Effectue automatique du débogueur appelé serveur attacher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `guidPort`  
 [in] Toujours défini sur `GUID_NULL`.  
  
 `dwPid`  
 [in] ID de processus, normalement récupéré avec la `GetCurrentProcessId` (fonction).  
  
 `dwProgramType`  
 [in] Type de programme : `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, ou `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] ID de programme.  
  
 `pszSessionId`  
 [in] Chaîne passée par le verbe debug.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** DbgAutoAttach.h  
  
## <a name="see-also"></a>Voir aussi

- [IDebugAutoAttach, interface](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
