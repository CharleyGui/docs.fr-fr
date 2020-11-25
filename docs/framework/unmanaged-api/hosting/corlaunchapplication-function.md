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
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704069"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="c987b-102">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="c987b-102">CorLaunchApplication Function</span></span>

<span data-ttu-id="c987b-103">Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="c987b-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="c987b-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c987b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c987b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c987b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c987b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c987b-106">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="c987b-107">dans Valeur de l’énumération [HOST_TYPE](host-type-enumeration.md) qui spécifie le type d’hôte qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="c987b-107">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="c987b-108">dans Nom complet de l’application en cours de lancement.</span><span class="sxs-lookup"><span data-stu-id="c987b-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="c987b-109">dans Nombre de chemins d’accès de manifeste pour l’application.</span><span class="sxs-lookup"><span data-stu-id="c987b-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="c987b-110">dans Tableau de chaînes, chacune spécifiant un chemin d’accès à un manifeste pour l’application en cours de lancement.</span><span class="sxs-lookup"><span data-stu-id="c987b-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="c987b-111">dans Nombre d’éléments de données d’activation pour l’application en cours de lancement.</span><span class="sxs-lookup"><span data-stu-id="c987b-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="c987b-112">dans Tableau de chaînes, chacune d’entre elles étant un élément de données d’activation pour l’application en cours de lancement.</span><span class="sxs-lookup"><span data-stu-id="c987b-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="c987b-113">à Pointeur vers des informations sur le processus dans lequel l’application a été chargée.</span><span class="sxs-lookup"><span data-stu-id="c987b-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c987b-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c987b-114">Requirements</span></span>  

 <span data-ttu-id="c987b-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c987b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c987b-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c987b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c987b-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c987b-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c987b-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c987b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c987b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c987b-119">See also</span></span>

- [<span data-ttu-id="c987b-120">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c987b-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
