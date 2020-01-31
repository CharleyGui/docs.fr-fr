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
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792539"
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
  
## <a name="parameters"></a>Parameters  
 `address`  
 dans Valeur `CORDB_ADDRESS` qui est l’adresse de base de la zone mémoire dans laquelle les données sont écrites. Avant le transfert de données, le système vérifie que la zone mémoire de la taille spécifiée, en commençant à l’adresse de base, est accessible en écriture. S’il n’est pas accessible, la méthode échoue.  
  
 `size`  
 dans Nombre d’octets à écrire dans la zone mémoire.  
  
 `buffer`  
 dans Mémoire tampon qui contient les données à écrire.  
  
 `written`  
 à Pointeur vers une variable qui reçoit le nombre d’octets écrits dans la zone mémoire de ce processus. Si `written` a la valeur NULL, ce paramètre est ignoré.  
  
## <a name="remarks"></a>Notes  
 Les données sont écrites automatiquement derrière des points d’arrêt. Dans la version .NET Framework 2,0, les débogueurs natifs ne doivent pas utiliser cette méthode pour injecter des points d’arrêt dans le flux d’instructions. Utilisez [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md) à la place.  
  
 La méthode `WriteMemory` doit être utilisée uniquement en dehors du code managé. Cette méthode peut endommager le runtime si elle est utilisée de manière incorrecte.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
