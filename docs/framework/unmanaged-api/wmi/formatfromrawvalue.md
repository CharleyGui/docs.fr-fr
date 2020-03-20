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
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="82716-103">FormatFromRawValue, fonction</span><span class="sxs-lookup"><span data-stu-id="82716-103">FormatFromRawValue function</span></span>
<span data-ttu-id="82716-104">Convertit une valeur de données de performances brute au format spécifié, ou deux valeurs de données de performances brutes si la conversion de format est basé sur l’heure.</span><span class="sxs-lookup"><span data-stu-id="82716-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="82716-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82716-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="82716-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82716-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="82716-107">[dans] Le type de compteur.</span><span class="sxs-lookup"><span data-stu-id="82716-107">[in] The counter type.</span></span> <span data-ttu-id="82716-108">Pour une liste de types de compteurs, voir [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="82716-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="82716-109">`dwCounterType`peut être n’importe `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`quel type de compteur excepté et .</span><span class="sxs-lookup"><span data-stu-id="82716-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="82716-110">[dans] Le format pour convertir les données brutes de performance.</span><span class="sxs-lookup"><span data-stu-id="82716-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="82716-111">Ce peut être l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="82716-111">It can be one of the following values:</span></span>

|<span data-ttu-id="82716-112">Constant</span><span class="sxs-lookup"><span data-stu-id="82716-112">Constant</span></span>  |<span data-ttu-id="82716-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="82716-113">Value</span></span>  |<span data-ttu-id="82716-114">Description</span><span class="sxs-lookup"><span data-stu-id="82716-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="82716-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="82716-115">0x00000200</span></span> | <span data-ttu-id="82716-116">Retournez la valeur calculée comme valeur flottante à double précision.</span><span class="sxs-lookup"><span data-stu-id="82716-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="82716-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="82716-117">0x00000400</span></span> | <span data-ttu-id="82716-118">Retournez la valeur calculée comme un intégrant 64 bits.</span><span class="sxs-lookup"><span data-stu-id="82716-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="82716-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="82716-119">0x00000100</span></span> | <span data-ttu-id="82716-120">Retournez la valeur calculée comme un intégrant 32 bits.</span><span class="sxs-lookup"><span data-stu-id="82716-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="82716-121">L’une des valeurs précédentes peut être ORed avec l’un des drapeaux de mise à l’échelle suivants:</span><span class="sxs-lookup"><span data-stu-id="82716-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="82716-122">Constant</span><span class="sxs-lookup"><span data-stu-id="82716-122">Constant</span></span>  |<span data-ttu-id="82716-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="82716-123">Value</span></span>  |<span data-ttu-id="82716-124">Description</span><span class="sxs-lookup"><span data-stu-id="82716-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="82716-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="82716-125">0x00001000</span></span> | <span data-ttu-id="82716-126">N’appliquez pas les facteurs de mise à l’échelle du compteur.</span><span class="sxs-lookup"><span data-stu-id="82716-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="82716-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="82716-127">0x00002000</span></span> | <span data-ttu-id="82716-128">Multipliez la valeur finale par 1 000.</span><span class="sxs-lookup"><span data-stu-id="82716-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="82716-129">[dans] Un pointeur à la base de temps, si nécessaire pour la conversion du format.</span><span class="sxs-lookup"><span data-stu-id="82716-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="82716-130">Si les informations de base de temps ne sont pas nécessaires pour la conversion du format, la valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="82716-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="82716-131">[dans] Un pointeur [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) vers une structure qui représente une valeur de performance brute.</span><span class="sxs-lookup"><span data-stu-id="82716-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="82716-132">[dans] Un pointeur [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) vers une structure qui représente une deuxième valeur de performance brute.</span><span class="sxs-lookup"><span data-stu-id="82716-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="82716-133">Si une deuxième valeur brute de performance `null`n’est pas nécessaire, ce paramètre doit être .</span><span class="sxs-lookup"><span data-stu-id="82716-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="82716-134">[out] Un pointeur [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) vers une structure qui reçoit la valeur de performance formatée.</span><span class="sxs-lookup"><span data-stu-id="82716-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="82716-135">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="82716-135">Return value</span></span>

<span data-ttu-id="82716-136">Les valeurs suivantes sont retournées par cette fonction :</span><span class="sxs-lookup"><span data-stu-id="82716-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="82716-137">Constant</span><span class="sxs-lookup"><span data-stu-id="82716-137">Constant</span></span>  |<span data-ttu-id="82716-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="82716-138">Value</span></span>  |<span data-ttu-id="82716-139">Description</span><span class="sxs-lookup"><span data-stu-id="82716-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="82716-140">0</span><span class="sxs-lookup"><span data-stu-id="82716-140">0</span></span> | <span data-ttu-id="82716-141">L’appel de fonction est réussi.</span><span class="sxs-lookup"><span data-stu-id="82716-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="82716-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="82716-142">0xC0000BBD</span></span> | <span data-ttu-id="82716-143">Un argument requis est manquant ou incorrect.</span><span class="sxs-lookup"><span data-stu-id="82716-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="82716-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="82716-144">0xC0000BBC</span></span> | <span data-ttu-id="82716-145">Le manche n’est pas un objet PDH valide.</span><span class="sxs-lookup"><span data-stu-id="82716-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="82716-146">Notes </span><span class="sxs-lookup"><span data-stu-id="82716-146">Remarks</span></span>

<span data-ttu-id="82716-147">Cette fonction enveloppe un appel à la fonction [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="82716-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="82716-148">Spécifications</span><span class="sxs-lookup"><span data-stu-id="82716-148">Requirements</span></span>

 <span data-ttu-id="82716-149">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82716-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="82716-150">**Bibliothèque:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="82716-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="82716-151">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82716-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="82716-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82716-152">See also</span></span>

- [<span data-ttu-id="82716-153">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="82716-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
