---
title: CorExitProcess, fonction
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: f6d8114732a3b7c15d0a0258a28a362d661b030a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673623"
---
# <a name="corexitprocess-function"></a>CorExitProcess, fonction

Arrête le processus non managé actuel.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Utilisez la méthode [ICLRMetaHost :: ExitProcess](iclrmetahost-exitprocess-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `exitCode`  
 Entier qui spécifie le code de sortie du processus.  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> À partir du .NET Framework 4, `CorExitProcess` quitte chaque Runtime démarré dans le processus, pas seulement le runtime auquel les API héritées ont été liées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
