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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442122"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach, méthode
Exécute l’attachement automatique du débogueur appelé par le serveur.  
  
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
 dans Toujours défini sur `GUID_NULL` .  
  
 `dwPid`  
 dans ID de processus, normalement récupéré avec la `GetCurrentProcessId` fonction.  
  
 `dwProgramType`  
 dans Type de programme : `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` ou `AUTOATTACH_PROGRAM_UNKNOWN` .  
  
 `dwProgramId`  
 dans ID de programme.  
  
 `pszSessionId`  
 dans Chaîne passée par le verbe Debug.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** DbgAutoAttach. h  
  
## <a name="see-also"></a>Voir aussi

- [IDebugAutoAttach, interface](idebugautoattach-interface.md)
