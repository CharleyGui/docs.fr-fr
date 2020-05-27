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
ms.openlocfilehash: a05cbe985c2cfebb67756fdfb54398b36e87f441
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008510"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="bb3bc-102">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="bb3bc-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="bb3bc-103">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="bb3bc-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3bc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb3bc-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bb3bc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb3bc-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="bb3bc-107">dans Identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-107">[in] A culture identifier.</span></span> <span data-ttu-id="bb3bc-108">Pass-1 pour `lcid` pour utiliser la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="bb3bc-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="bb3bc-110">à Mémoire tampon qui contient le message d’erreur une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="bb3bc-111">dans Taille de la mémoire tampon du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="bb3bc-112">dans Pas.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="bb3bc-113">à Pointeur vers la longueur du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb3bc-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bb3bc-114">Return Value</span></span>  
 <span data-ttu-id="bb3bc-115">Cette méthode retourne des codes d’erreur COM standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="bb3bc-116">Code de retour</span><span class="sxs-lookup"><span data-stu-id="bb3bc-116">Return code</span></span>|<span data-ttu-id="bb3bc-117">Description</span><span class="sxs-lookup"><span data-stu-id="bb3bc-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bb3bc-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb3bc-118">S_OK</span></span>|<span data-ttu-id="bb3bc-119">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="bb3bc-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bb3bc-120">E_INVALIDARG</span></span>|<span data-ttu-id="bb3bc-121">`szBuffer`a la valeur null, ou `iMax` est égal à zéro (0).</span><span class="sxs-lookup"><span data-stu-id="bb3bc-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb3bc-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb3bc-122">Remarks</span></span>  
 <span data-ttu-id="bb3bc-123">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="bb3bc-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3bc-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bb3bc-124">Requirements</span></span>  
 <span data-ttu-id="bb3bc-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb3bc-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3bc-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb3bc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb3bc-127">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bb3bc-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3bc-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3bc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3bc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb3bc-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bb3bc-130">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="bb3bc-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="bb3bc-131">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="bb3bc-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
