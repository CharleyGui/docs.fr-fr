---
title: VerifyClientKey (fonction) (référence des API non managées)
description: La fonction VerifyClientKey garantit que la clé du client a la sécurité correcte.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b51fe4510f4172227d9afd049eb6815790a165
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783084"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey (fonction)
Garantit que la clé du client offre une sécurité correcte.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est `ERROR_SUCCESS` (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *WinError.h*.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.def  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
