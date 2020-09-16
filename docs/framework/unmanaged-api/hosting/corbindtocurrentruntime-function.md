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
ms.openlocfilehash: 9c5d83b5f2ffb06c9fb14f715a3ea7ff12319086
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547827"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="659cc-102">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="659cc-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="659cc-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="659cc-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="659cc-104">Le format du fichier XML est modélisé après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="659cc-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="659cc-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="659cc-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="659cc-106">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="659cc-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="659cc-107">Consultez [chargement du Common Language Runtime dans un processus](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="659cc-107">See [Loading the Common Language Runtime into a Process](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659cc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="659cc-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="659cc-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="659cc-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="659cc-110">dans Nom d’un fichier de configuration d’application qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="659cc-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="659cc-111">Si le nom de fichier n’est pas qualifié complet, il est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="659cc-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="659cc-112">La version du runtime à charger est décrite par l’attribut version dans l' [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="659cc-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="659cc-113">Si aucune version n’est spécifiée, ou si l' `<requiredRuntime>` élément est introuvable, la dernière version du CLR qui est installée sur l’ordinateur est chargée.</span><span class="sxs-lookup"><span data-stu-id="659cc-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="659cc-114">dans `CLSID` De la coclasse qui implémente l’interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="659cc-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="659cc-115">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="659cc-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="659cc-116">dans `IID` De l’interface que vous demandez.</span><span class="sxs-lookup"><span data-stu-id="659cc-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="659cc-117">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="659cc-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="659cc-118">à Pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="659cc-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="659cc-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="659cc-119">Requirements</span></span>  
 <span data-ttu-id="659cc-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="659cc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="659cc-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="659cc-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="659cc-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="659cc-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="659cc-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="659cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659cc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="659cc-124">See also</span></span>

- [<span data-ttu-id="659cc-125">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="659cc-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="659cc-126">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="659cc-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="659cc-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="659cc-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="659cc-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="659cc-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="659cc-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="659cc-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="659cc-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
