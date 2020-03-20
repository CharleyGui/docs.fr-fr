---
title: CorBindToRuntimeByCfg, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178247"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="630d2-102">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="630d2-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="630d2-103">Charge l’heure d’exécution de la langue commune (CLR) dans un processus en utilisant des informations de version qui sont lues à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="630d2-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="630d2-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="630d2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630d2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="630d2-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="630d2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="630d2-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="630d2-107">[dans] Un pointeur `IStream` vers un objet qui lit le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="630d2-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="630d2-108">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="630d2-108">[in] Reserved for future use.</span></span> <span data-ttu-id="630d2-109">Utilisez 0 (zéro) comme valeur.</span><span class="sxs-lookup"><span data-stu-id="630d2-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="630d2-110">[dans] Une valeur de [l’énumération STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) qui spécifie le comportement de démarrage du CLR.</span><span class="sxs-lookup"><span data-stu-id="630d2-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="630d2-111">[dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="630d2-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="630d2-112">Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="630d2-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="630d2-113">[dans] L’interface `IID` `ICorRuntimeHost` ou `ICLRRuntimeHost` l’interface.</span><span class="sxs-lookup"><span data-stu-id="630d2-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="630d2-114">Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="630d2-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="630d2-115">[out] Un pointeur à l’adresse de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="630d2-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="630d2-116">Notes </span><span class="sxs-lookup"><span data-stu-id="630d2-116">Remarks</span></span>  
 <span data-ttu-id="630d2-117">Le format du fichier XML est calqué sur le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="630d2-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="630d2-118">Pour plus d’informations sur les fichiers XML, voir [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="630d2-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="630d2-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="630d2-119">Requirements</span></span>  
 <span data-ttu-id="630d2-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="630d2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="630d2-121">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="630d2-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="630d2-122">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="630d2-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="630d2-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="630d2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630d2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="630d2-124">See also</span></span>

- [<span data-ttu-id="630d2-125">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="630d2-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="630d2-126">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="630d2-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="630d2-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="630d2-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="630d2-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="630d2-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="630d2-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="630d2-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="630d2-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="630d2-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
