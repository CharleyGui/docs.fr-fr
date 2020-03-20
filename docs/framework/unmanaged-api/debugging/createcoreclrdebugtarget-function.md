---
title: Fonction CreateCoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179217"
---
# <a name="createcoreclrdebugtarget-function"></a>Fonction CreateCoreClrDebugTarget
Crée une connexion à un proxy de débbugger qui fonctionne sur une machine à distance, et renvoie un objet [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) qui peut être utilisé pour interroger les processus d’exécution et les temps d’exécution chargés sur la machine à distance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwAddress`  
 [in] Adresse IPv4 d'un ordinateur cible distant.  
  
 `ppTarget`  
 [out] Pointeur à un pointeur à un objet [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) qui sera créé.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppTarget`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Bibliothèque:** mscordbi_macx86.dll  
  
 **Versions cadre .NET:** 3.5 SP1
