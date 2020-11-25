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
ms.openlocfilehash: 5da4eaa459c515689b822e4cb537380245e800e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722763"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="0350d-103">GetErrorInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="0350d-103">GetErrorInfo function</span></span>

<span data-ttu-id="0350d-104">Récupère les informations d’erreur à partir de l’appel de fonction précédent.</span><span class="sxs-lookup"><span data-stu-id="0350d-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0350d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0350d-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="0350d-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0350d-106">Return value</span></span>

<span data-ttu-id="0350d-107">Pointeur vers un objet [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) si l’appel de fonction réussit, ou en `null` cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="0350d-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0350d-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0350d-108">Remarks</span></span>

<span data-ttu-id="0350d-109">Cette fonction encapsule un appel à la méthode [IComThreadingInfo :: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="0350d-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0350d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0350d-110">Requirements</span></span>  

 <span data-ttu-id="0350d-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0350d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0350d-112">**En-tête :** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="0350d-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="0350d-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0350d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0350d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0350d-114">See also</span></span>

- [<span data-ttu-id="0350d-115">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="0350d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
