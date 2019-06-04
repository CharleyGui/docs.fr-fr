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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07d2f08792b6fdea28bd56045de8da30ab552a4f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490573"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="3a778-102">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="3a778-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="3a778-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version qui sont lu à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3a778-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="3a778-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3a778-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a778-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a778-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a778-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a778-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="3a778-107">[in] Un pointeur vers un `IStream` objet qui lit le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3a778-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="3a778-108">[in] Réservé pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3a778-108">[in] Reserved for future use.</span></span> <span data-ttu-id="3a778-109">Utilisez 0 (zéro) comme valeur.</span><span class="sxs-lookup"><span data-stu-id="3a778-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="3a778-110">[in] Une valeur de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération qui spécifie le comportement de démarrage du CLR.</span><span class="sxs-lookup"><span data-stu-id="3a778-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3a778-111">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="3a778-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3a778-112">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="3a778-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3a778-113">[in] Le `IID` de soit le `ICorRuntimeHost` ou `ICLRRuntimeHost` interface.</span><span class="sxs-lookup"><span data-stu-id="3a778-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="3a778-114">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="3a778-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3a778-115">[out] Pointeur vers l’adresse de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="3a778-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a778-116">Notes</span><span class="sxs-lookup"><span data-stu-id="3a778-116">Remarks</span></span>  
 <span data-ttu-id="3a778-117">Le format du fichier XML est modélisé d’après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="3a778-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="3a778-118">Pour plus d’informations sur les fichiers XML, consultez [schéma de fichier de Configuration](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a778-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a778-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3a778-119">Requirements</span></span>  
 <span data-ttu-id="3a778-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a778-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a778-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a778-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a778-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a778-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a778-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a778-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a778-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a778-124">See also</span></span>

- [<span data-ttu-id="3a778-125">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="3a778-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3a778-126">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="3a778-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="3a778-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="3a778-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="3a778-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="3a778-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="3a778-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="3a778-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="3a778-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="3a778-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
