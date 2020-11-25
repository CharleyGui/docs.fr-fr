---
title: Fonction GetCurrentApartmentType (référence des API non managées)
description: La fonction GetCurrentApartmentType récupère le type de cloisonnement dans lequel l’appelant s’exécute.
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
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726195"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="58051-103">GetCurrentApartmentType, fonction</span><span class="sxs-lookup"><span data-stu-id="58051-103">GetCurrentApartmentType function</span></span>

<span data-ttu-id="58051-104">Récupère le type de cloisonnement dans lequel l’appelant s’exécute.</span><span class="sxs-lookup"><span data-stu-id="58051-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="58051-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58051-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="58051-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58051-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="58051-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="58051-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="58051-108">dans Pointeur vers une instance [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="58051-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="58051-109">à Pointeur vers une valeur d’énumération [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) qui indique le cloisonnement de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="58051-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="58051-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="58051-110">Return value</span></span>

|<span data-ttu-id="58051-111">Constante</span><span class="sxs-lookup"><span data-stu-id="58051-111">Constant</span></span>  |<span data-ttu-id="58051-112">Value</span><span class="sxs-lookup"><span data-stu-id="58051-112">Value</span></span>  |<span data-ttu-id="58051-113">Description</span><span class="sxs-lookup"><span data-stu-id="58051-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="58051-114">0</span><span class="sxs-lookup"><span data-stu-id="58051-114">0</span></span> | <span data-ttu-id="58051-115">La fonction s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="58051-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="58051-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="58051-116">0x80000008</span></span> | <span data-ttu-id="58051-117">L’appelant ne s’exécute pas dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="58051-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="58051-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="58051-118">Remarks</span></span>

<span data-ttu-id="58051-119">Cette fonction encapsule un appel à la méthode [IComThreadingInfo :: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="58051-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="58051-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58051-120">Requirements</span></span>  

 <span data-ttu-id="58051-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58051-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58051-122">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="58051-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="58051-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58051-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58051-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58051-124">See also</span></span>

- [<span data-ttu-id="58051-125">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="58051-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
