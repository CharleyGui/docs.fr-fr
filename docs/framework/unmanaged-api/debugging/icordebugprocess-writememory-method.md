---
title: ICorDebugProcess::WriteMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599bf310a0b819bc662b90a5a86e87ac27c37b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737019"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory, méthode
Écrit des données dans une zone de mémoire dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 [in] Un `CORDB_ADDRESS` valeur qui est l’adresse de base de la zone de mémoire dans lequel des données est écrites. Avant le transfert de données se produit, le système vérifie que la zone de mémoire de la taille spécifiée, en commençant à l’adresse de base, est accessible en écriture. Si elle n’est pas accessible, la méthode échoue.  
  
 `size`  
 [in] Le nombre d’octets à écrire dans la zone de mémoire.  
  
 `buffer`  
 [in] Une mémoire tampon qui contient les données à écrire.  
  
 `written`  
 [out] Pointeur vers une variable qui reçoit le nombre d’octets écrits dans la zone de mémoire dans ce processus. Si `written` est NULL, ce paramètre est ignoré.  
  
## <a name="remarks"></a>Notes  
 Données sont automatiquement écrites derrière les points d’arrêt. Dans le .NET Framework version 2.0, les débogueurs natifs n’employez pas cette méthode pour injecter des points d’arrêt dans le flux d’instructions. Utilisez [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) à la place.  
  
 Le `WriteMemory` méthode doit être utilisée uniquement en dehors du code managé. Cette méthode peut endommager le runtime pour une utilisation incorrecte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
