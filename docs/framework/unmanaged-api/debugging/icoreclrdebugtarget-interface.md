---
title: Interface ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397157"
---
# <a name="icoreclrdebugtarget-interface"></a>Interface ICorDebugDataTarget
Fournit des méthodes qui contrôlent les décomptes de références, énumèrent les processus et libèrent la mémoire associée à un débogueur attaché à une cible Silverlight Macintosh à distance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md)|Énumère les processus en cours d'exécution sur un ordinateur distant.|  
|[Méthode ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md)|Énumère les CLR (Common Language Runtime) dans le processus spécifié sur un ordinateur distant.|  
|[Méthode ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md)|Libère la mémoire allouée par les méthodes d’énumération de cette classe.|  
  
## <a name="remarks"></a>Notes  
 Actuellement, cette fonctionnalité est prise en charge uniquement pour le débogage d’une cible d’application Silverlight qui s’exécute sur un ordinateur Macintosh distant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86. dll  
  
 **Versions de .NET Framework :** 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemoteTarget, interface](icordebugremotetarget-interface.md)
- [ICorDebug, interface](icordebug-interface.md)

- [Interfaces de débogage](debugging-interfaces.md)
