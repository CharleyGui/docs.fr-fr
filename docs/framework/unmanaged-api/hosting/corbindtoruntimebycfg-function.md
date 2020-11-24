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
ms.openlocfilehash: d319382b577844a804c3e4562676491a15de5f63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673772"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="84bc9-102">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="84bc9-102">CorBindToRuntimeByCfg Function</span></span>

<span data-ttu-id="84bc9-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version lues à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="84bc9-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="84bc9-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="84bc9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84bc9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84bc9-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="84bc9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="84bc9-106">Parameters</span></span>  

 `pCfgStream`  
 <span data-ttu-id="84bc9-107">dans Pointeur vers un `IStream` objet qui lit le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="84bc9-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="84bc9-108">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="84bc9-108">[in] Reserved for future use.</span></span> <span data-ttu-id="84bc9-109">Utilisez 0 (zéro) comme valeur.</span><span class="sxs-lookup"><span data-stu-id="84bc9-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="84bc9-110">dans Valeur de l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) qui spécifie le comportement de démarrage du CLR.</span><span class="sxs-lookup"><span data-stu-id="84bc9-110">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="84bc9-111">dans `CLSID` De la coclasse qui implémente l’interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="84bc9-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="84bc9-112">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="84bc9-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="84bc9-113">dans `IID` De l' `ICorRuntimeHost` `ICLRRuntimeHost` interface ou.</span><span class="sxs-lookup"><span data-stu-id="84bc9-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="84bc9-114">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="84bc9-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="84bc9-115">à Pointeur vers l’adresse de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="84bc9-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84bc9-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="84bc9-116">Remarks</span></span>  

 <span data-ttu-id="84bc9-117">Le format du fichier XML est modélisé après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="84bc9-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="84bc9-118">Pour plus d’informations sur les fichiers XML, consultez [schéma du fichier de configuration](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="84bc9-118">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84bc9-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="84bc9-119">Requirements</span></span>  

 <span data-ttu-id="84bc9-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84bc9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84bc9-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84bc9-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84bc9-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84bc9-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84bc9-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84bc9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bc9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84bc9-124">See also</span></span>

- [<span data-ttu-id="84bc9-125">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="84bc9-125">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="84bc9-126">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="84bc9-126">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="84bc9-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="84bc9-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="84bc9-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="84bc9-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="84bc9-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="84bc9-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="84bc9-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="84bc9-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
