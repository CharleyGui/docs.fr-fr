---
title: Fonction ResetSecurity (Référence API non gestion)
description: La fonction ResetSecurity attribue un jeton d’imitation au fil actuel.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174860"
---
# <a name="resetsecurity-function"></a>ResetSecurity, fonction
Assigne le jeton d’emprunt d’identité fourni au thread actif.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a>Paramètres

`token`  
[dans] Le jeton d’imitation pour s’associer au fil actuel. Sa valeur peut être `null`.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, `S_OK` la valeur de rendement est (0).

Si la fonction échoue, la valeur de retour est un code d’erreur non nul. Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
