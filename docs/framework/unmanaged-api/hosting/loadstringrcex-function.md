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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5520aef09c72819ff2b3763cd43af13f013263c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490208"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="2c057-102">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="2c057-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="2c057-103">Traduit une valeur HRESULT à un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2c057-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="2c057-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2c057-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c057-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c057-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c057-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c057-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2c057-107">[in] Identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="2c057-107">[in] A culture identifier.</span></span> <span data-ttu-id="2c057-108">Passez -1 `lcid` pour utiliser la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="2c057-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="2c057-109">[in] Une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2c057-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2c057-110">[out] Une mémoire tampon qui contient le message d’erreur en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="2c057-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="2c057-111">[in] La taille de la mémoire tampon de message.</span><span class="sxs-lookup"><span data-stu-id="2c057-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="2c057-112">[in] Ignoré.</span><span class="sxs-lookup"><span data-stu-id="2c057-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="2c057-113">[out] Pointeur vers la longueur du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c057-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c057-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2c057-114">Return Value</span></span>  
 <span data-ttu-id="2c057-115">Cette méthode retourne des codes d’erreur COM standards, tel que défini dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="2c057-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2c057-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="2c057-116">Return code</span></span>|<span data-ttu-id="2c057-117">Description</span><span class="sxs-lookup"><span data-stu-id="2c057-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2c057-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c057-118">S_OK</span></span>|<span data-ttu-id="2c057-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="2c057-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="2c057-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2c057-120">E_INVALIDARG</span></span>|<span data-ttu-id="2c057-121">`szBuffer` a la valeur null, ou `iMax` est zéro (0).</span><span class="sxs-lookup"><span data-stu-id="2c057-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c057-122">Notes</span><span class="sxs-lookup"><span data-stu-id="2c057-122">Remarks</span></span>  
 <span data-ttu-id="2c057-123">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="2c057-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c057-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c057-124">Requirements</span></span>  
 <span data-ttu-id="2c057-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c057-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c057-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c057-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c057-127">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c057-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c057-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c057-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c057-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c057-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2c057-130">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="2c057-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="2c057-131">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="2c057-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
