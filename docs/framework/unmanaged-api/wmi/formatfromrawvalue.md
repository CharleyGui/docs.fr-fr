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
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="70bcd-103">FormatFromRawValue, fonction</span><span class="sxs-lookup"><span data-stu-id="70bcd-103">FormatFromRawValue function</span></span>
<span data-ttu-id="70bcd-104">Convertit une valeur de données de performances brute au format spécifié, ou deux valeurs de données de performances brutes si la conversion de format est basé sur l’heure.</span><span class="sxs-lookup"><span data-stu-id="70bcd-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="70bcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70bcd-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="70bcd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="70bcd-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="70bcd-107">[in] Le type de compteur.</span><span class="sxs-lookup"><span data-stu-id="70bcd-107">[in] The counter type.</span></span> <span data-ttu-id="70bcd-108">Pour obtenir la liste des types de compteurs, consultez [Types de compteurs de performances WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="70bcd-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="70bcd-109">`dwCounterType` peut être n’importe quel type de compteur à l’exception de `PERF_LARGE_RAW_FRACTION` et `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="70bcd-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="70bcd-110">[in] Le format dans lequel convertir les données de performances brutes.</span><span class="sxs-lookup"><span data-stu-id="70bcd-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="70bcd-111">Il peut prendre l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="70bcd-111">It can be one of the following values:</span></span>

|<span data-ttu-id="70bcd-112">Constante</span><span class="sxs-lookup"><span data-stu-id="70bcd-112">Constant</span></span>  |<span data-ttu-id="70bcd-113">`Value`</span><span class="sxs-lookup"><span data-stu-id="70bcd-113">Value</span></span>  |<span data-ttu-id="70bcd-114">Description</span><span class="sxs-lookup"><span data-stu-id="70bcd-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="70bcd-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="70bcd-115">0x00000200</span></span> | <span data-ttu-id="70bcd-116">Retourne la valeur calculée en tant que valeur à virgule flottante double précision.</span><span class="sxs-lookup"><span data-stu-id="70bcd-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="70bcd-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="70bcd-117">0x00000400</span></span> | <span data-ttu-id="70bcd-118">Retourne la valeur calculée sous forme d’entier 64 bits.</span><span class="sxs-lookup"><span data-stu-id="70bcd-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="70bcd-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="70bcd-119">0x00000100</span></span> | <span data-ttu-id="70bcd-120">Retourne la valeur calculée sous forme d’entier 32 bits.</span><span class="sxs-lookup"><span data-stu-id="70bcd-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="70bcd-121">Une des valeurs précédentes peut être ORed avec l’un des indicateurs de mise à l’échelle suivants :</span><span class="sxs-lookup"><span data-stu-id="70bcd-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="70bcd-122">Constante</span><span class="sxs-lookup"><span data-stu-id="70bcd-122">Constant</span></span>  |<span data-ttu-id="70bcd-123">`Value`</span><span class="sxs-lookup"><span data-stu-id="70bcd-123">Value</span></span>  |<span data-ttu-id="70bcd-124">Description</span><span class="sxs-lookup"><span data-stu-id="70bcd-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="70bcd-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="70bcd-125">0x00001000</span></span> | <span data-ttu-id="70bcd-126">N’appliquez pas les facteurs d’échelle du compteur.</span><span class="sxs-lookup"><span data-stu-id="70bcd-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="70bcd-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="70bcd-127">0x00002000</span></span> | <span data-ttu-id="70bcd-128">Multiplie la valeur finale par 1 000.</span><span class="sxs-lookup"><span data-stu-id="70bcd-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="70bcd-129">[in] Pointeur vers la base de temps, si nécessaire pour la conversion de format.</span><span class="sxs-lookup"><span data-stu-id="70bcd-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="70bcd-130">Si les informations de base de temps ne sont pas nécessaires pour la conversion de format, la valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="70bcd-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="70bcd-131">`pRawValue1`\ [in] pointeur vers un [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure qui représente une valeur de performances brutes.</span><span class="sxs-lookup"><span data-stu-id="70bcd-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="70bcd-132">[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure qui représente une seconde valeur de performances brutes.</span><span class="sxs-lookup"><span data-stu-id="70bcd-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="70bcd-133">Si une seconde valeur de performances brutes n’est pas nécessaire, ce paramètre doit être `null`.</span><span class="sxs-lookup"><span data-stu-id="70bcd-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="70bcd-134">[out] Un pointeur vers un [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure qui reçoit la valeur de performance de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="70bcd-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="70bcd-135">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="70bcd-135">Return value</span></span>

<span data-ttu-id="70bcd-136">Les valeurs suivantes sont retournées par cette fonction :</span><span class="sxs-lookup"><span data-stu-id="70bcd-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="70bcd-137">Constante</span><span class="sxs-lookup"><span data-stu-id="70bcd-137">Constant</span></span>  |<span data-ttu-id="70bcd-138">`Value`</span><span class="sxs-lookup"><span data-stu-id="70bcd-138">Value</span></span>  |<span data-ttu-id="70bcd-139">Description</span><span class="sxs-lookup"><span data-stu-id="70bcd-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="70bcd-140">0</span><span class="sxs-lookup"><span data-stu-id="70bcd-140">0</span></span> | <span data-ttu-id="70bcd-141">L’appel de fonction est réussi.</span><span class="sxs-lookup"><span data-stu-id="70bcd-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="70bcd-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="70bcd-142">0xC0000BBD</span></span> | <span data-ttu-id="70bcd-143">Un argument requis est manquant ou incorrect.</span><span class="sxs-lookup"><span data-stu-id="70bcd-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="70bcd-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="70bcd-144">0xC0000BBC</span></span> | <span data-ttu-id="70bcd-145">Le handle n’est pas un objet PDH valide.</span><span class="sxs-lookup"><span data-stu-id="70bcd-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="70bcd-146">Notes</span><span class="sxs-lookup"><span data-stu-id="70bcd-146">Remarks</span></span>

<span data-ttu-id="70bcd-147">Cette fonction encapsule un appel à la [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) (fonction).</span><span class="sxs-lookup"><span data-stu-id="70bcd-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="70bcd-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="70bcd-148">Requirements</span></span>

 <span data-ttu-id="70bcd-149">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70bcd-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="70bcd-150">**Bibliothèque :** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="70bcd-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="70bcd-151">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="70bcd-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="70bcd-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70bcd-152">See also</span></span>

- [<span data-ttu-id="70bcd-153">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="70bcd-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
