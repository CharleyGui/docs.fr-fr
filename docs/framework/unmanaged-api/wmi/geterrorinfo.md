---
title: Fonction GetErrorInfo (référence API non gestion)
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
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176810"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="ffeab-103">GetErrorInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="ffeab-103">GetErrorInfo function</span></span>
<span data-ttu-id="ffeab-104">Récupère les informations d’erreur à partir de l’appel de fonction précédent.</span><span class="sxs-lookup"><span data-stu-id="ffeab-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ffeab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffeab-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="ffeab-106">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ffeab-106">Return value</span></span>

<span data-ttu-id="ffeab-107">Un pointeur vers un objet [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) si `null` l’appel de fonction réussit, ou s’il échoue.</span><span class="sxs-lookup"><span data-stu-id="ffeab-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ffeab-108">Notes </span><span class="sxs-lookup"><span data-stu-id="ffeab-108">Remarks</span></span>

<span data-ttu-id="ffeab-109">Cette fonction enveloppe un appel à la méthode [IComThreadingInfo::GetErrorInfo.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="ffeab-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffeab-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ffeab-110">Requirements</span></span>  
 <span data-ttu-id="ffeab-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffeab-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffeab-112">**En-tête:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="ffeab-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="ffeab-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ffeab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffeab-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffeab-114">See also</span></span>

- [<span data-ttu-id="ffeab-115">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="ffeab-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
