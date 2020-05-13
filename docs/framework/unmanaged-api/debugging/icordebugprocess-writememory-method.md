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
ms.openlocfilehash: 0a433ccb81ef62ac92a4553a838a2c98a04fc7c1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212813"
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
 dans `CORDB_ADDRESS`Valeur qui est l’adresse de base de la zone mémoire dans laquelle les données sont écrites. Avant le transfert de données, le système vérifie que la zone mémoire de la taille spécifiée, en commençant à l’adresse de base, est accessible en écriture. S’il n’est pas accessible, la méthode échoue.  
  
 `size`  
 dans Nombre d’octets à écrire dans la zone mémoire.  
  
 `buffer`  
 dans Mémoire tampon qui contient les données à écrire.  
  
 `written`  
 à Pointeur vers une variable qui reçoit le nombre d’octets écrits dans la zone mémoire de ce processus. Si `written` a la valeur null, ce paramètre est ignoré.  
  
## <a name="remarks"></a>Remarks  
 Les données sont écrites automatiquement derrière des points d’arrêt. Dans la version .NET Framework 2,0, les débogueurs natifs ne doivent pas utiliser cette méthode pour injecter des points d’arrêt dans le flux d’instructions. Utilisez [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md) à la place.  
  
 La `WriteMemory` méthode doit être utilisée uniquement en dehors du code managé. Cette méthode peut endommager le runtime si elle est utilisée de manière incorrecte.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
