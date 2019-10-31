---
title: GetVersionFromProcess, fonction
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: 76c033b11f3212241827d74f4fe18ee881f20b64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127037"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="c9d35-102">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="c9d35-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="c9d35-103">Obtient le numéro de version du common language runtime (CLR) associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9d35-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="c9d35-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c9d35-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d35-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9d35-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9d35-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="c9d35-107">dans Handle d’un processus.</span><span class="sxs-lookup"><span data-stu-id="c9d35-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c9d35-108">à Mémoire tampon qui contient la chaîne de numéro de version en cas d’achèvement réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c9d35-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c9d35-109">dans Longueur de la mémoire tampon de version.</span><span class="sxs-lookup"><span data-stu-id="c9d35-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="c9d35-110">à Pointeur vers la longueur de la chaîne de numéro de version.</span><span class="sxs-lookup"><span data-stu-id="c9d35-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9d35-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9d35-111">Return Value</span></span>  
 <span data-ttu-id="c9d35-112">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="c9d35-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c9d35-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="c9d35-113">Return code</span></span>|<span data-ttu-id="c9d35-114">Description</span><span class="sxs-lookup"><span data-stu-id="c9d35-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c9d35-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9d35-115">S_OK</span></span>|<span data-ttu-id="c9d35-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="c9d35-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9d35-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c9d35-117">E_INVALIDARG</span></span>|<span data-ttu-id="c9d35-118">`pVersion` a la valeur null et `cchBuffer` n’a pas la valeur null, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="c9d35-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="c9d35-119">ou</span><span class="sxs-lookup"><span data-stu-id="c9d35-119">-or-</span></span><br /><br /> <span data-ttu-id="c9d35-120">`hProcess` n’est pas un handle valide d’un processus.</span><span class="sxs-lookup"><span data-stu-id="c9d35-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="c9d35-121">ou</span><span class="sxs-lookup"><span data-stu-id="c9d35-121">-or-</span></span><br /><br /> <span data-ttu-id="c9d35-122">Le CLR n’est pas chargé.</span><span class="sxs-lookup"><span data-stu-id="c9d35-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="c9d35-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c9d35-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c9d35-124">`cchBuffer` est null ou inférieur à la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="c9d35-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="c9d35-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c9d35-125">E_NOTIMPL</span></span>|<span data-ttu-id="c9d35-126">Cette méthode n’est pas disponible sur le système d’exploitation Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="c9d35-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9d35-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="c9d35-127">Requirements</span></span>  
 <span data-ttu-id="c9d35-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d35-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d35-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9d35-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9d35-130">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9d35-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9d35-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d35-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d35-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d35-132">See also</span></span>

- [<span data-ttu-id="c9d35-133">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="c9d35-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="c9d35-134">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="c9d35-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="c9d35-135">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="c9d35-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
