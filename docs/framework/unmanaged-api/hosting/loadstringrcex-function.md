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
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177983"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="4c452-102">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="4c452-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="4c452-103">Traduit une valeur HRESULT à un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4c452-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="4c452-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="4c452-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c452-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c452-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4c452-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c452-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="4c452-107">[dans] Un identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="4c452-107">[in] A culture identifier.</span></span> <span data-ttu-id="4c452-108">Passer -1 `lcid` pour utiliser la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c452-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="4c452-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4c452-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="4c452-110">[out] Un tampon qui contient le message d’erreur une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="4c452-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="4c452-111">[dans] La taille du tampon de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4c452-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="4c452-112">[dans] Ignoré.</span><span class="sxs-lookup"><span data-stu-id="4c452-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="4c452-113">[out] Un pointeur sur la longueur du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4c452-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c452-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c452-114">Return Value</span></span>  
 <span data-ttu-id="4c452-115">Cette méthode renvoie les codes d’erreur COM standard, tels que définis dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="4c452-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="4c452-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="4c452-116">Return code</span></span>|<span data-ttu-id="4c452-117">Description</span><span class="sxs-lookup"><span data-stu-id="4c452-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4c452-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c452-118">S_OK</span></span>|<span data-ttu-id="4c452-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="4c452-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="4c452-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4c452-120">E_INVALIDARG</span></span>|<span data-ttu-id="4c452-121">`szBuffer`est nul, `iMax` ou est nul (0).</span><span class="sxs-lookup"><span data-stu-id="4c452-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c452-122">Notes </span><span class="sxs-lookup"><span data-stu-id="4c452-122">Remarks</span></span>  
 <span data-ttu-id="4c452-123">Si la méthode ne `szBuffer` se termine pas avec succès, contient une ficelle vide.</span><span class="sxs-lookup"><span data-stu-id="4c452-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c452-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c452-124">Requirements</span></span>  
 <span data-ttu-id="4c452-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c452-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c452-126">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="4c452-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c452-127">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="4c452-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c452-128">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c452-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c452-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c452-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4c452-130">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="4c452-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="4c452-131">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="4c452-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
