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
ms.openlocfilehash: 26cffe9936f2e01078b6f54e8499b58519f1018e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729419"
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

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. def  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
