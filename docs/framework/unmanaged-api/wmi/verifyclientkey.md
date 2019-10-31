---
title: Fonction VerifyClientKey (référence des API non managées)
description: La fonction VerifyClientKey garantit la sécurité de la clé client.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107360"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey fonction)
Garantit que la clé du client offre une sécurité correcte.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est `ERROR_SUCCESS` (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *winerror. h*.

## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. def  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
