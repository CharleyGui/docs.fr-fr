---
title: ICLRDataTarget::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179183"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext, méthode
Obtient le contexte d’exécution actuel pour le thread donné dans le processus cible. Cette méthode est appelée par les services d’accès aux données de l’heure courante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 [dans] L’identifiant du système d’exploitation d’un thread dans le processus cible.  
  
 `contextFlags`  
 [dans] Drapeaux qui précisent quelles parties du contexte revenir. La mise en œuvre reviendra au moins dans ces parties du contexte.  
  
 `contextSize`  
 [dans] La taille du contexte.  
  
 `context`  
 [out] Pointeur vers un tampon dans lequel placer le contexte.  
  
 Les données `context` dans le tampon doivent être dans `CONTEXT` le format de la structure Win32. Le contexte spécifie les données d’enregistrement spécifiques `CONTEXT` au processeur, de sorte que la définition de la structure Win32 dépend de l’architecture du processeur. Consultez le fichier d’en-tête WinNT.h `CONTEXT` pour la définition de la structure Win32.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
