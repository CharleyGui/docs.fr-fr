---
title: FormatFromRawValue fonction (Référence API non gestion)
description: La fonction FormatFromRawValue convertit les données de performance brutes en un format spécifié.
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
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176836"
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
[dans] Le type de compteur. Pour une liste de types de compteurs, voir [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`peut être n’importe `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`quel type de compteur excepté et .

`dwFormat`\
[dans] Le format pour convertir les données brutes de performance. Ce peut être l’une des valeurs suivantes :

|Constant  |Valeur  |Description |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retournez la valeur calculée comme valeur flottante à double précision. |
| `PDH_FMT_LARGE` | 0x00000400 | Retournez la valeur calculée comme un intégrant 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retournez la valeur calculée comme un intégrant 32 bits. |

L’une des valeurs précédentes peut être ORed avec l’un des drapeaux de mise à l’échelle suivants:

|Constant  |Valeur  |Description |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | N’appliquez pas les facteurs de mise à l’échelle du compteur. |
| `PDH_FMT_1000` | 0x00002000 | Multipliez la valeur finale par 1 000. |

`pTimeBase`\
[dans] Un pointeur à la base de temps, si nécessaire pour la conversion du format. Si les informations de base de temps ne sont pas nécessaires pour la conversion du format, la valeur de ce paramètre est ignorée.

`pRawValue1`\
[dans] Un pointeur [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) vers une structure qui représente une valeur de performance brute.

`pRawValue2`\
[dans] Un pointeur [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) vers une structure qui représente une deuxième valeur de performance brute. Si une deuxième valeur brute de performance `null`n’est pas nécessaire, ce paramètre doit être .

`pFmtValue`\
[out] Un pointeur [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) vers une structure qui reçoit la valeur de performance formatée.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes sont retournées par cette fonction :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | L’appel de fonction est réussi. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Un argument requis est manquant ou incorrect. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Le manche n’est pas un objet PDH valide. |

## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à la fonction [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **Bibliothèque:** PerfCounter.dll

 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
