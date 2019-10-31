---
title: LoadStringRCEx, fonction
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: 68332aee895f012bcf6ab6a72936c8dddc7f28a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122045"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="155fa-102">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="155fa-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="155fa-103">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="155fa-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="155fa-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="155fa-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="155fa-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="155fa-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="155fa-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="155fa-107">dans Identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="155fa-107">[in] A culture identifier.</span></span> <span data-ttu-id="155fa-108">Pass-1 pour `lcid` pour utiliser la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="155fa-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="155fa-109">dans HRESULT.</span><span class="sxs-lookup"><span data-stu-id="155fa-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="155fa-110">à Mémoire tampon qui contient le message d’erreur une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="155fa-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="155fa-111">dans Taille de la mémoire tampon du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="155fa-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="155fa-112">dans Pas.</span><span class="sxs-lookup"><span data-stu-id="155fa-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="155fa-113">à Pointeur vers la longueur du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="155fa-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="155fa-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="155fa-114">Return Value</span></span>  
 <span data-ttu-id="155fa-115">Cette méthode retourne des codes d’erreur COM standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="155fa-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="155fa-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="155fa-116">Return code</span></span>|<span data-ttu-id="155fa-117">Description</span><span class="sxs-lookup"><span data-stu-id="155fa-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="155fa-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="155fa-118">S_OK</span></span>|<span data-ttu-id="155fa-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="155fa-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="155fa-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="155fa-120">E_INVALIDARG</span></span>|<span data-ttu-id="155fa-121">`szBuffer` a la valeur null, ou `iMax` est égal à zéro (0).</span><span class="sxs-lookup"><span data-stu-id="155fa-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="155fa-122">Notes</span><span class="sxs-lookup"><span data-stu-id="155fa-122">Remarks</span></span>  
 <span data-ttu-id="155fa-123">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="155fa-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="155fa-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="155fa-124">Requirements</span></span>  
 <span data-ttu-id="155fa-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155fa-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155fa-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="155fa-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="155fa-127">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="155fa-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="155fa-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="155fa-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155fa-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="155fa-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="155fa-130">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="155fa-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="155fa-131">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="155fa-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
