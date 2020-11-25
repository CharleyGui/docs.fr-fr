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
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721879"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="a6edc-102">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="a6edc-102">GetVersionFromProcess Function</span></span>

<span data-ttu-id="a6edc-103">Obtient le numéro de version du common language runtime (CLR) associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6edc-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="a6edc-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a6edc-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6edc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6edc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6edc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6edc-106">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="a6edc-107">dans Handle d’un processus.</span><span class="sxs-lookup"><span data-stu-id="a6edc-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a6edc-108">à Mémoire tampon qui contient la chaîne de numéro de version en cas d’achèvement réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a6edc-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a6edc-109">dans Longueur de la mémoire tampon de version.</span><span class="sxs-lookup"><span data-stu-id="a6edc-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a6edc-110">à Pointeur vers la longueur de la chaîne de numéro de version.</span><span class="sxs-lookup"><span data-stu-id="a6edc-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6edc-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a6edc-111">Return Value</span></span>  

 <span data-ttu-id="a6edc-112">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="a6edc-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a6edc-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="a6edc-113">Return code</span></span>|<span data-ttu-id="a6edc-114">Description</span><span class="sxs-lookup"><span data-stu-id="a6edc-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a6edc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6edc-115">S_OK</span></span>|<span data-ttu-id="a6edc-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="a6edc-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a6edc-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a6edc-117">E_INVALIDARG</span></span>|<span data-ttu-id="a6edc-118">`pVersion` a la valeur null et `cchBuffer` n’est pas null, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="a6edc-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="a6edc-119">- ou -</span><span class="sxs-lookup"><span data-stu-id="a6edc-119">-or-</span></span><br /><br /> <span data-ttu-id="a6edc-120">`hProcess` n’est pas un handle valide pour un processus.</span><span class="sxs-lookup"><span data-stu-id="a6edc-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="a6edc-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="a6edc-121">-or-</span></span><br /><br /> <span data-ttu-id="a6edc-122">Le CLR n’est pas chargé.</span><span class="sxs-lookup"><span data-stu-id="a6edc-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="a6edc-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a6edc-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a6edc-124">`cchBuffer` est null ou inférieur à la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="a6edc-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="a6edc-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a6edc-125">E_NOTIMPL</span></span>|<span data-ttu-id="a6edc-126">Cette méthode n’est pas disponible sur le système d’exploitation Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="a6edc-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6edc-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6edc-127">Requirements</span></span>  

 <span data-ttu-id="a6edc-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6edc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6edc-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6edc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6edc-130">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6edc-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6edc-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6edc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6edc-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6edc-132">See also</span></span>

- [<span data-ttu-id="a6edc-133">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="a6edc-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="a6edc-134">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="a6edc-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="a6edc-135">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="a6edc-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
