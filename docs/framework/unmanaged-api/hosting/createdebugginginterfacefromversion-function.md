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
ms.openlocfilehash: 6f5eec282aec6a2757664023ce8031410e316f10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501844"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="5bc74-102">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="5bc74-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="5bc74-103">Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5bc74-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="5bc74-104">Cette fonction est obsolète dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5bc74-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="5bc74-105">Au lieu de cela, pour obtenir une interface pour le common language runtime (CLR) 2,0, utilisez la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) et spécifiez l’identificateur de classe CLSID_CLRDebuggingLegacy et l’identificateur d’interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="5bc74-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="5bc74-106">Pour obtenir une interface pour CLR 4 ou version ultérieure, appelez la fonction [CLRCreateInstance](clrcreateinstance-function.md) et spécifiez l’identificateur de classe CLSID_CLRDebugging et l’identificateur d’interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="5bc74-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc74-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bc74-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc74-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5bc74-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="5bc74-109">dans Version de `ICorDebug` qui est attendue par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="5bc74-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="5bc74-110">Consultez l’énumération [CorDebugInterfaceVersion,](../debugging/cordebuginterfaceversion-enumeration.md) pour connaître les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="5bc74-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="5bc74-111">dans Version de common language runtime associée à l’application ou au processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="5bc74-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="5bc74-112">Pour plus d’informations sur la récupération de cette valeur, consultez la méthode [GetVersionFromProcess](getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5bc74-112">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="5bc74-113">à Emplacement qui reçoit un pointeur vers l' `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="5bc74-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc74-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5bc74-114">Return Value</span></span>  
 <span data-ttu-id="5bc74-115">Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans le fichier WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="5bc74-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="5bc74-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="5bc74-116">Return code</span></span>|<span data-ttu-id="5bc74-117">Description</span><span class="sxs-lookup"><span data-stu-id="5bc74-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5bc74-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bc74-118">S_OK</span></span>|<span data-ttu-id="5bc74-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="5bc74-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="5bc74-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5bc74-120">E_INVALIDARG</span></span>|<span data-ttu-id="5bc74-121">`szDebuggeeVersion`ou `ppCordb` est null, ou la chaîne de version est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="5bc74-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc74-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="5bc74-122">Remarks</span></span>  
 <span data-ttu-id="5bc74-123">Le `szDebuggeeVersion` paramètre est mappé à la version correspondante de mscordbi. dll.</span><span class="sxs-lookup"><span data-stu-id="5bc74-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc74-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5bc74-124">Requirements</span></span>  
 <span data-ttu-id="5bc74-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc74-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc74-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5bc74-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bc74-127">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5bc74-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bc74-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc74-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc74-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bc74-129">See also</span></span>

- [<span data-ttu-id="5bc74-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="5bc74-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
