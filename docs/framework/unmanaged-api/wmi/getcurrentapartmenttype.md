---
title: Fonction GetCurrentApartmentType (Référence API non gestion)
description: La fonction GetCurrentApartmentType récupère le type d’appartement dans lequel l’appelant exécute.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176823"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="4c8f5-103">GetCurrentApartmentType, fonction</span><span class="sxs-lookup"><span data-stu-id="4c8f5-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="4c8f5-104">Récupère le type de cloisonnement dans lequel l’appelant s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4c8f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c8f5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="4c8f5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c8f5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c8f5-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4c8f5-108">[dans] Un pointeur à une instance [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)</span><span class="sxs-lookup"><span data-stu-id="4c8f5-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="4c8f5-109">[out] Un pointeur à une valeur de recensement [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) qui indique l’appartement de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c8f5-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4c8f5-110">Return value</span></span>

|<span data-ttu-id="4c8f5-111">Constant</span><span class="sxs-lookup"><span data-stu-id="4c8f5-111">Constant</span></span>  |<span data-ttu-id="4c8f5-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="4c8f5-112">Value</span></span>  |<span data-ttu-id="4c8f5-113">Description</span><span class="sxs-lookup"><span data-stu-id="4c8f5-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="4c8f5-114">0</span><span class="sxs-lookup"><span data-stu-id="4c8f5-114">0</span></span> | <span data-ttu-id="4c8f5-115">La fonction s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="4c8f5-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="4c8f5-116">0x80000008</span></span> | <span data-ttu-id="4c8f5-117">L’appelant ne s’exécute pas dans un appartement.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="4c8f5-118">Notes </span><span class="sxs-lookup"><span data-stu-id="4c8f5-118">Remarks</span></span>

<span data-ttu-id="4c8f5-119">Cette fonction enveloppe un appel à [l’IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) méthode.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c8f5-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c8f5-120">Requirements</span></span>  
 <span data-ttu-id="4c8f5-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c8f5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c8f5-122">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c8f5-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c8f5-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c8f5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8f5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c8f5-124">See also</span></span>

- [<span data-ttu-id="4c8f5-125">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="4c8f5-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
