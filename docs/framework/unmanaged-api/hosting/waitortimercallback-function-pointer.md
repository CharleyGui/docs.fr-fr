---
title: WAITORTIMERCALLBACK (pointeur fonction)
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: ee5dd611888ec52e360ef45fab4c01e9c5b2d6bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009446"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK (pointeur fonction)
Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente ( <xref:System.Threading.WaitHandle> ) a été signalé ou a expiré.  
  
 Ce pointeur de fonction est déconseillé dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `lpParameter`  
 dans Pointeur vers un objet qui contient les informations définies par l’hôte.  
  
 `TimerOrWaitFired`  
 [in] `true` Si le handle d’attente a expiré ou `false` s’il a été signalé.  
  
## <a name="remarks"></a>Remarques  
 La fonction vers laquelle `WAITORTIMERCALLBACK` pointe est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorWks. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
