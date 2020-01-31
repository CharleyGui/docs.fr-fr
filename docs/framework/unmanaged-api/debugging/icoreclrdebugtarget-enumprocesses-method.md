---
title: Méthode ICoreClrDebugTarget::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 11b1072b3467f7d0a3f223fbc2151ec9ccf461ad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790802"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>Méthode ICoreClrDebugTarget::EnumProcesses
Énumère les processus en cours d'exécution sur un ordinateur distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pcProcs`  
 [out] Nombre de processus retournés dans `ppProcs`. Cette valeur peut être égale à 0 (zéro).  
  
 `ppProcs`  
 à Tableau de structures [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) qui représentent les processus en cours d’exécution sur l’ordinateur distant.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Opération réussie.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppProcs`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Notes  
 Pour libérer la mémoire allouée par cette méthode, appelez la méthode [ICoreClrDebugTarget :: FreeMemory](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86. dll  
  
 **Versions de .NET Framework :** 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICoreClrDebugTarget, interface](icoreclrdebugtarget-interface.md)
