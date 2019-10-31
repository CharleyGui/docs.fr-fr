---
title: CorBindToCurrentRuntime, fonction
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138320"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="8ceff-102">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="8ceff-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="8ceff-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8ceff-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="8ceff-104">Le format du fichier XML est modélisé après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="8ceff-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="8ceff-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ceff-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="8ceff-106">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8ceff-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="8ceff-107">Consultez [chargement du Common Language Runtime dans un processus](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8ceff-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ceff-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ceff-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ceff-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ceff-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="8ceff-110">dans Nom d’un fichier de configuration d’application qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="8ceff-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="8ceff-111">Si le nom de fichier n’est pas qualifié complet, il est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="8ceff-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="8ceff-112">La version du runtime à charger est décrite par l’attribut version dans l’élément [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8ceff-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="8ceff-113">Si aucune version n’est spécifiée, ou si l’élément `<requiredRuntime>` est introuvable, la dernière version du CLR qui est installée sur l’ordinateur est chargée.</span><span class="sxs-lookup"><span data-stu-id="8ceff-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="8ceff-114">dans `CLSID` de la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8ceff-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="8ceff-115">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8ceff-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="8ceff-116">dans `IID` de l’interface que vous demandez.</span><span class="sxs-lookup"><span data-stu-id="8ceff-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="8ceff-117">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8ceff-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8ceff-118">à Pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="8ceff-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ceff-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="8ceff-119">Requirements</span></span>  
 <span data-ttu-id="8ceff-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ceff-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ceff-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ceff-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ceff-122">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ceff-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ceff-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ceff-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ceff-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ceff-124">See also</span></span>

- [<span data-ttu-id="8ceff-125">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="8ceff-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="8ceff-126">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="8ceff-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="8ceff-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="8ceff-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="8ceff-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="8ceff-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="8ceff-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="8ceff-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="8ceff-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="8ceff-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
