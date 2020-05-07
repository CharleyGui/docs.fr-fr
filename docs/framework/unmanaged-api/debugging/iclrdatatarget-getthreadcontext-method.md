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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860603"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext, méthode
Obtient le contexte d’exécution actuel du thread donné dans le processus cible. Cette méthode est appelée par les services d’accès aux données common language runtime.  
  
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
 dans Identificateur de système d’exploitation d’un thread dans le processus cible.  
  
 `contextFlags`  
 dans Indicateurs qui spécifient les parties du contexte à retourner. L’implémentation renverra au moins ces parties du contexte.  
  
 `contextSize`  
 dans Taille du contexte.  
  
 `context`  
 à Pointeur vers une mémoire tampon dans laquelle placer le contexte.  
  
 Les données de la `context` mémoire tampon doivent être au format de la structure `CONTEXT` Win32. Le contexte spécifie des données de Registre spécifiques au processeur, donc la définition `CONTEXT` de la structure Win32 dépend de l’architecture du processeur. Reportez-vous au fichier d’en-tête Winnt. `CONTEXT` h pour la définition de la structure Win32.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
