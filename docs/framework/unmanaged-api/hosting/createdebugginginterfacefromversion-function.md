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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176446"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="b3631-102">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="b3631-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="b3631-103">Crée un objet [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) basé sur les informations de version spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b3631-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="b3631-104">Cette fonction est obsolète dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="b3631-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="b3631-105">Au lieu de cela, pour obtenir une interface pour l’heure de fonctionnement de la langue commune (CLR) 2.0, utilisez la méthode [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) et spécifier l’identifiant de classe CLSID_CLRDebuggingLegacy et l’identifiant d’interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="b3631-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="b3631-106">Pour obtenir une interface pour CLR 4 ou plus tard, appelez la fonction [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) et spécifiez l’identifiant de classe CLSID_CLRDebugging et l’identifiant d’interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="b3631-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3631-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3631-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3631-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3631-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="b3631-109">[dans] La version `ICorDebug` de cela est attendue par le débbugger.</span><span class="sxs-lookup"><span data-stu-id="b3631-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="b3631-110">Voir le recensement [de CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) pour les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="b3631-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="b3631-111">[dans] La version courante de l’heure d’exécution de langue associée à l’application ou au processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="b3631-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="b3631-112">Consultez la méthode [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) pour plus d’informations sur la récupération de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="b3631-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="b3631-113">[out] L’emplacement qui reçoit `ICorDebug` un pointeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b3631-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3631-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b3631-114">Return Value</span></span>  
 <span data-ttu-id="b3631-115">Cette méthode renvoie les codes d’erreur COM standard tels que définis dans le fichier WinError.h en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b3631-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="b3631-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="b3631-116">Return code</span></span>|<span data-ttu-id="b3631-117">Description</span><span class="sxs-lookup"><span data-stu-id="b3631-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b3631-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3631-118">S_OK</span></span>|<span data-ttu-id="b3631-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="b3631-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="b3631-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b3631-120">E_INVALIDARG</span></span>|<span data-ttu-id="b3631-121">`szDebuggeeVersion`ou `ppCordb` est nul, ou la chaîne de version est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="b3631-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3631-122">Notes </span><span class="sxs-lookup"><span data-stu-id="b3631-122">Remarks</span></span>  
 <span data-ttu-id="b3631-123">Les `szDebuggeeVersion` cartes de paramètres à la version correspondante de MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="b3631-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3631-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b3631-124">Requirements</span></span>  
 <span data-ttu-id="b3631-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3631-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3631-126">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="b3631-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3631-127">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="b3631-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3631-128">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3631-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3631-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3631-129">See also</span></span>

- [<span data-ttu-id="b3631-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="b3631-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
