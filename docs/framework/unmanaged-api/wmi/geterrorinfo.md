---
title: Fonction GetErrorInfo (référence des API non managées)
description: La fonction GetErrorInfo récupère les informations d’erreur de l’appel de fonction précédent.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9a80c0b5522113e704336cda29362a0406077931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553673"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="d7311-103">GetErrorInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="d7311-103">GetErrorInfo function</span></span>
<span data-ttu-id="d7311-104">Récupère les informations d’erreur à partir de l’appel de fonction précédent.</span><span class="sxs-lookup"><span data-stu-id="d7311-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d7311-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7311-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="d7311-106">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d7311-106">Return value</span></span>

<span data-ttu-id="d7311-107">Pointeur vers un objet [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) si l’appel de fonction réussit, ou en `null` cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="d7311-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d7311-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d7311-108">Remarks</span></span>

<span data-ttu-id="d7311-109">Cette fonction encapsule un appel à la méthode [IComThreadingInfo :: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="d7311-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7311-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d7311-110">Requirements</span></span>  
 <span data-ttu-id="d7311-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7311-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7311-112">**En-tête :** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="d7311-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="d7311-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7311-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7311-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7311-114">See also</span></span>

- [<span data-ttu-id="d7311-115">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="d7311-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
