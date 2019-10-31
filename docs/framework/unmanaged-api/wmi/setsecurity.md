---
title: Fonction SetSecurity (référence des API non managées)
description: La fonction SetSecurity récupère le jeton d’emprunt d’identité du thread actuel.
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
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120224"
---
# <a name="setsecurity-function"></a>SetSecurity fonction)

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
à Quand la fonction retourne une valeur, contient un pointeur vers une `boolean` qui indique si le jeton doit être réinitialisé en appelant la fonction [ResetSecurity](resetsecurity.md) .

`token`\
à Quand la fonction retourne une valeur, contient un pointeur vers le handle du jeton d’emprunt d’identité associé au thread actuel. Sa valeur peut être `null` s’il n’y a aucun jeton associé au thread actuel. 

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est `S_OK` (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro. Pour afficher les informations d’erreur étendues, appelez la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** WMINet_Utils. idl

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
