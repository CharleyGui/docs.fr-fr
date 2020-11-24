---
title: Méthode ICoreClrDebugTarget::EnumRuntimes
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 093f49508e8e96a4003f1aab8eed59e2fd196ba9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679271"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>Méthode ICoreClrDebugTarget::EnumRuntimes

Énumère les CLR (Common Language Runtime) dans le processus spécifié en cours d'exécution sur un ordinateur distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwInternalProcessID`  
 [in] ID de processus interne du processus pour lequel vous souhaitez énumérer les runtimes. Ce sera `m_dwInternalID` le [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)correspondant.  
  
 `pcRuntimes`  
 [out] Nombre de runtimes retournés dans `ppRuntimes`. Cette valeur peut être égale à 0 (zéro).  
  
 `ppRuntimes`  
 à Tableau de structures [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) qui représentent les runtimes chargés dans le processus cible distant.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK  
 Réussite.  
  
 S_FALSE  
 `dwInternalProcessID` ne correspond à aucun processus qui s'exécute sur l'ordinateur, probablement parce que le processus a été arrêté. `pcRuntimes` et `ppRuntimes` sont null.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppRuntimes`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Remarques  

 Pour libérer la mémoire allouée par cette méthode, appelez la méthode [ICoreClrDebugTarget :: FreeMemory](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions de .NET Framework :** 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [Interface ICorDebugDataTarget](icoreclrdebugtarget-interface.md)
