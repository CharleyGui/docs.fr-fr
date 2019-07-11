---
title: ICorDebugProcess2::SetUnmanagedBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a5d1bad80a5aad8573508aab5fbf98c8c2a03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736838"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint, méthode
Définit un point d’arrêt non managé à l’offset d’image native spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 [in] Un `CORDB_ADDRESS` objet qui spécifie le décalage de l’image native.  
  
 `bufsize`  
 [in] La taille, en octets, de la `buffer` tableau.  
  
 `buffer`  
 [out] Tableau qui contient le code d’opération qui est remplacé par le point d’arrêt.  
  
 `bufLen`  
 [out] Un pointeur vers le nombre d’octets retournés dans le `buffer` tableau.  
  
## <a name="remarks"></a>Notes  
 Si le décalage de l’image native est dans le common language runtime (CLR), le point d’arrêt sera ignoré. Ainsi, le CLR afin d’éviter la distribution d’un point d’arrêt hors-bande, lorsque le point d’arrêt est défini par le débogueur.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
