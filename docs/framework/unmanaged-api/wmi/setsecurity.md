---
title: Fonction SetSecurity (Référence API non gestion)
description: La fonction SetSecurity récupère le jeton d’imitation du fil actuel.
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176732"
---
# <a name="setsecurity-function"></a>SetSecurity, fonction

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
[out] Lorsque la fonction revient, `boolean` contient un pointeur à un qui indique si le jeton doit être réinitialisé en appelant la fonction [ResetSecurity.](resetsecurity.md)

`token`\
[out] Lorsque la fonction revient, contient un pointeur à la poignée du jeton d’imitation associé au thread actuel. Sa valeur `null` peut être s’il n’y a pas de jeton associé au fil actuel.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, `S_OK` la valeur de rendement est (0).

Si la fonction échoue, la valeur de retour est un code d’erreur non nul. Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête:** WMINet_Utils.idl

 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
