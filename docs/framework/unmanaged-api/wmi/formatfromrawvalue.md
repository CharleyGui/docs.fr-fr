---
title: FormatFromRawValue, fonction (référence des API non managées)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47f92122eddf3cc8e6aec19d75fd2a95f76e9973
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746697"
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
[in] Le type de compteur. Pour obtenir la liste des types de compteurs, consultez [Types de compteurs de performances WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` peut être n’importe quel type de compteur à l’exception de `PERF_LARGE_RAW_FRACTION` et `PERF_LARGE_RAW_BASE`. 

`dwFormat`\
[in] Le format dans lequel convertir les données de performances brutes. Il peut prendre l’une des valeurs suivantes :

|Constante  |`Value`  |Description |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retourne la valeur calculée en tant que valeur à virgule flottante double précision. | 
| `PDH_FMT_LARGE` | 0x00000400 | Retourne la valeur calculée sous forme d’entier 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retourne la valeur calculée sous forme d’entier 32 bits. |

Une des valeurs précédentes peut être ORed avec l’un des indicateurs de mise à l’échelle suivants :

|Constante  |`Value`  |Description |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | N’appliquez pas les facteurs d’échelle du compteur. |
| `PDH_FMT_1000` | 0x00002000 | Multiplie la valeur finale par 1 000. | 

`pTimeBase`\
[in] Pointeur vers la base de temps, si nécessaire pour la conversion de format. Si les informations de base de temps ne sont pas nécessaires pour la conversion de format, la valeur de ce paramètre est ignorée.

`pRawValue1`\ [in] pointeur vers un [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure qui représente une valeur de performances brutes.

`pRawValue2`\
[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure qui représente une seconde valeur de performances brutes. Si une seconde valeur de performances brutes n’est pas nécessaire, ce paramètre doit être `null`.

`pFmtValue`\
[out] Un pointeur vers un [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure qui reçoit la valeur de performance de mise en forme.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes sont retournées par cette fonction :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | L’appel de fonction est réussi. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Un argument requis est manquant ou incorrect. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Le handle n’est pas un objet PDH valide. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) (fonction).

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **Bibliothèque :** PerfCounter.dll

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
