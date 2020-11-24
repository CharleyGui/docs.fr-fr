---
title: Fonction FormatFromRawValue (référence des API non managées)
description: La fonction FormatFromRawValue convertit les données de performances brutes dans un format spécifié.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e678aca5baf82c07ec9fc5c85cef22630af5ab0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672329"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue, fonction

Convertit une valeur de données de performances brute au format spécifié, ou deux valeurs de données de performances brutes si la conversion de format est basé sur l’heure.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a>Paramètres

`dwCounterType`\
dans Type de compteur. Pour obtenir la liste des types de compteurs, consultez [types de compteurs de performance WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` peut être n’importe quel type de compteur à l’exception de `PERF_LARGE_RAW_FRACTION` et `PERF_LARGE_RAW_BASE` .

`dwFormat`\
dans Format dans lequel convertir les données de performances brutes. Ce peut être l’une des valeurs suivantes :

|Constante  |Value  |Description |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retourne la valeur calculée sous la forme d’une valeur à virgule flottante double précision. |
| `PDH_FMT_LARGE` | 0x00000400 | Retourne la valeur calculée sous la forme d’un entier 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retourne la valeur calculée sous la forme d’un entier 32 bits. |

L’une des valeurs précédentes peut être associée à l’un des indicateurs de mise à l’échelle suivants :

|Constante  |Value  |Description |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | N’appliquez pas les facteurs de mise à l’échelle du compteur. |
| `PDH_FMT_1000` | 0x00002000 | Multipliez la valeur finale par 1 000. |

`pTimeBase`\
dans Pointeur vers la base de temps, si nécessaire pour la conversion de format. Si les informations de base de temps ne sont pas nécessaires pour la conversion de format, la valeur de ce paramètre est ignorée.

`pRawValue1`\
dans Pointeur vers une [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure qui représente une valeur de performance brute.

`pRawValue2`\
dans Pointeur vers une [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure qui représente une deuxième valeur de performance brute. Si une deuxième valeur de performance brute n’est pas nécessaire, ce paramètre doit être `null` .

`pFmtValue`\
à Pointeur vers une [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure qui reçoit la valeur de performance mise en forme.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes sont retournées par cette fonction :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | L’appel de la fonction a réussi. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Un argument requis est manquant ou incorrect. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Le descripteur n’est pas un objet PDH valide. |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la fonction [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) .

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **Bibliothèque :** PerfCounter.dll

 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
