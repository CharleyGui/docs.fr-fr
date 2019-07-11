---
title: SetSecurity (fonction) (référence des API non managées)
description: La fonction SetSecurity récupère le jeton d’emprunt d’identité du thread actif.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb71263201c86a93ca0bfbd783f2b8512055e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783114"
---
# <a name="setsecurity-function"></a>SetSecurity (fonction)

Récupère le jeton d’emprunt d’identité associé au thread actif. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>Paramètres

`pNeedToReset`\
[out] Lorsque la fonction est retournée, contient un pointeur vers un `boolean` qui indique si le jeton doit être réinitialisé en appelant le [ResetSecurity](resetsecurity.md) (fonction).

`token`\
[out] Lorsque la fonction est retournée, contient un pointeur vers le handle du jeton d’emprunt d’identité associé au thread actuel. Sa valeur peut être `null` s’il n’existe aucun jeton associé au thread actuel. 

## <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est `S_OK` (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro. Pour obtenir les informations d’erreur étendues, appelez le [GetErrorInfo](geterrorinfo.md) (fonction).

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** WMINet_Utils.idl

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
