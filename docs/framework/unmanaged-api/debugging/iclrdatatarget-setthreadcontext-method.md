---
title: ICLRDataTarget::SetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179128"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext, méthode
Définit le contexte actuel du thread spécifié dans le processus cible. Cette méthode est appelée par les services d’accès aux données de l’heure courante (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 [dans] L’identifiant du système d’exploitation d’un thread dans le processus cible.  
  
 `contextSize`  
 [dans] La taille du contexte.  
  
 `context`  
 [dans] Pointeur vers un tampon contenant le contexte.  
  
 Les données `context` dans le tampon seront dans le `CONTEXT` format de la structure Win32. Le contexte spécifie les données d’enregistrement spécifiques `CONTEXT` au processeur, de sorte que la définition de la structure Win32 dépend de l’architecture du processeur. Consultez le fichier d’en-tête WinNT.h `CONTEXT` pour la définition de la structure Win32.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
