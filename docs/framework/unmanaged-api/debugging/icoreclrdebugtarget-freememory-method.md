---
title: Méthode ICoreClrDebugTarget::FreeMemory
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 061a2b9990d4b4d6398d0a31b97bc403a5f10de4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397168"
---
# <a name="icoreclrdebugtargetfreememory-method"></a>Méthode ICoreClrDebugTarget::FreeMemory
Libère la mémoire allouée par les méthodes [ICoreClrDebugTarget :: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) et [ICoreClrDebugTarget :: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pMemory`  
 dans Pointeur vers le tableau retourné par la méthode [ICoreClrDebugTarget :: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ou [ICoreClrDebugTarget :: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86. dll  
  
 **Versions de .NET Framework :** 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [Interface ICorDebugDataTarget](icoreclrdebugtarget-interface.md)
