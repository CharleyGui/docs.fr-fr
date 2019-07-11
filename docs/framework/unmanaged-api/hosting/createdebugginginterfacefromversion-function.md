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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe34ffded73e8305e4ade3bb9b402b1d8e1bcc49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764674"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="662c4-102">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="662c4-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="662c4-103">Crée un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objet basé sur les informations de version spécifié.</span><span class="sxs-lookup"><span data-stu-id="662c4-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="662c4-104">Cette fonction est obsolète dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="662c4-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="662c4-105">Pour obtenir une interface pour le common language runtime (CLR) 2.0, utilisez plutôt le [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) (méthode) et spécifiez l’identificateur de classe CLSID_CLRDebuggingLegacy et l’identificateur d’interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="662c4-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="662c4-106">Pour obtenir une interface pour le CLR 4 ou version ultérieure, appelez le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) de fonction et spécifier l’identificateur de classe CLSID_CLRDebugging et l’identificateur d’interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="662c4-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662c4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="662c4-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="662c4-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="662c4-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="662c4-109">[in] La version de `ICorDebug` qui est attendue par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="662c4-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="662c4-110">Consultez le [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) énumération pour les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="662c4-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="662c4-111">[in] Version du common language runtime associée à l’application ou le processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="662c4-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="662c4-112">Consultez le [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) méthode pour plus d’informations sur la récupération de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="662c4-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="662c4-113">[out] L’emplacement qui reçoit un pointeur vers le `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="662c4-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="662c4-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="662c4-114">Return Value</span></span>  
 <span data-ttu-id="662c4-115">Cette méthode retourne des codes d’erreur COM standard, tel que défini dans le fichier WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="662c4-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="662c4-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="662c4-116">Return code</span></span>|<span data-ttu-id="662c4-117">Description</span><span class="sxs-lookup"><span data-stu-id="662c4-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="662c4-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="662c4-118">S_OK</span></span>|<span data-ttu-id="662c4-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="662c4-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="662c4-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="662c4-120">E_INVALIDARG</span></span>|<span data-ttu-id="662c4-121">`szDebuggeeVersion` ou `ppCordb` est null, ou la version de chaîne est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="662c4-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="662c4-122">Notes</span><span class="sxs-lookup"><span data-stu-id="662c4-122">Remarks</span></span>  
 <span data-ttu-id="662c4-123">Le `szDebuggeeVersion` paramètre correspond à la version correspondante de MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="662c4-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="662c4-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="662c4-124">Requirements</span></span>  
 <span data-ttu-id="662c4-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="662c4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="662c4-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="662c4-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="662c4-127">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="662c4-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="662c4-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="662c4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662c4-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="662c4-129">See also</span></span>

- [<span data-ttu-id="662c4-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="662c4-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
