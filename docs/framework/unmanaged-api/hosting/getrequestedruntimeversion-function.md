---
title: GetRequestedRuntimeVersion, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178139"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="4fdbc-102">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fdbc-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="4fdbc-103">Obtient le numéro de version de l’heure d’exécution de langue commune (CLR) demandée par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="4fdbc-104">Si cette version n’est pas installée, obtient la version la plus récente qui est installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="4fdbc-105">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fdbc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fdbc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fdbc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4fdbc-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="4fdbc-108">[dans] Le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="4fdbc-109">[out] Un tampon qui contient la chaîne de numéro de version une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4fdbc-110">[dans] La longueur du tampon de version.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="4fdbc-111">[out] Un pointeur sur la longueur de la chaîne de numéro de version.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fdbc-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4fdbc-112">Return Value</span></span>  
 <span data-ttu-id="4fdbc-113">Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="4fdbc-114">Code de retour</span><span class="sxs-lookup"><span data-stu-id="4fdbc-114">Return code</span></span>|<span data-ttu-id="4fdbc-115">Description</span><span class="sxs-lookup"><span data-stu-id="4fdbc-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4fdbc-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fdbc-116">S_OK</span></span>|<span data-ttu-id="4fdbc-117">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="4fdbc-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4fdbc-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4fdbc-119">Le tampon de version n’est pas assez grand pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="4fdbc-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4fdbc-120">E_POINTER</span></span>|<span data-ttu-id="4fdbc-121">`pdwLength` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="4fdbc-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fdbc-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4fdbc-122">Requirements</span></span>  
 <span data-ttu-id="4fdbc-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fdbc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fdbc-124">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="4fdbc-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fdbc-125">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="4fdbc-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fdbc-126">**.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fdbc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdbc-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fdbc-127">See also</span></span>

- [<span data-ttu-id="4fdbc-128">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="4fdbc-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="4fdbc-129">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="4fdbc-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="4fdbc-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="4fdbc-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
