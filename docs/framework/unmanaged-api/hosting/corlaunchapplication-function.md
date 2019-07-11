---
title: CorLaunchApplication, fonction
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9861de733a9acb43c7e2a4b4941f9945fc5f0ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758373"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="00501-102">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="00501-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="00501-103">Démarre l’application sur le chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="00501-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="00501-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="00501-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00501-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00501-105">Syntax</span></span>  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00501-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00501-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="00501-107">[in] Une valeur de la [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) énumération qui spécifie le type d’hôte qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="00501-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="00501-108">[in] Le nom complet de l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="00501-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="00501-109">[in] Le nombre de chemins d’accès de manifestes pour l’application.</span><span class="sxs-lookup"><span data-stu-id="00501-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="00501-110">[in] Tableau de chaînes, dont chacun spécifie un chemin d’accès à un manifeste d’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="00501-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="00501-111">[in] Le nombre d’éléments de données d’activation pour l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="00501-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="00501-112">[in] Tableau de chaînes, chacune d’elles étant un élément de données d’activation pour l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="00501-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="00501-113">[out] Pointeur vers les informations sur le processus dans lequel l’application a été chargée.</span><span class="sxs-lookup"><span data-stu-id="00501-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00501-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00501-114">Requirements</span></span>  
 <span data-ttu-id="00501-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00501-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00501-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00501-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00501-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00501-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00501-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00501-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00501-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00501-119">See also</span></span>

- [<span data-ttu-id="00501-120">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="00501-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
