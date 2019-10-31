---
title: CreateDebuggingInterfaceFromVersion, fonction
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136838"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="8611a-102">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="8611a-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="8611a-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span><span class="sxs-lookup"><span data-stu-id="8611a-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="8611a-104">This function is obsolete in the .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8611a-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="8611a-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="8611a-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="8611a-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="8611a-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8611a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8611a-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8611a-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8611a-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="8611a-109">[in] The version of `ICorDebug` that is expected by the debugger.</span><span class="sxs-lookup"><span data-stu-id="8611a-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="8611a-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span><span class="sxs-lookup"><span data-stu-id="8611a-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="8611a-111">[in] The common language runtime version associated with the application or process to be debugged.</span><span class="sxs-lookup"><span data-stu-id="8611a-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="8611a-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span><span class="sxs-lookup"><span data-stu-id="8611a-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="8611a-113">[out] The location that receives a pointer to the `ICorDebug` object.</span><span class="sxs-lookup"><span data-stu-id="8611a-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8611a-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8611a-114">Return Value</span></span>  
 <span data-ttu-id="8611a-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span><span class="sxs-lookup"><span data-stu-id="8611a-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="8611a-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="8611a-116">Return code</span></span>|<span data-ttu-id="8611a-117">Description</span><span class="sxs-lookup"><span data-stu-id="8611a-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8611a-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8611a-118">S_OK</span></span>|<span data-ttu-id="8611a-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="8611a-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8611a-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8611a-120">E_INVALIDARG</span></span>|<span data-ttu-id="8611a-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span><span class="sxs-lookup"><span data-stu-id="8611a-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8611a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="8611a-122">Remarks</span></span>  
 <span data-ttu-id="8611a-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="8611a-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8611a-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="8611a-124">Requirements</span></span>  
 <span data-ttu-id="8611a-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8611a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8611a-126">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8611a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8611a-127">**Library:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8611a-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8611a-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8611a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8611a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8611a-129">See also</span></span>

- [<span data-ttu-id="8611a-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="8611a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
