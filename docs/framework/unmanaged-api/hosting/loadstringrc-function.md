---
title: LoadStringRC, fonction
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9047bf973224cdbc1f67463ef70f15f81089f827
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768457"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="bd7c9-102">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="bd7c9-102">LoadStringRC Function</span></span>
<span data-ttu-id="bd7c9-103">Traduit une valeur HRESULT dans un message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="bd7c9-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7c9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd7c9-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd7c9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd7c9-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="bd7c9-107">[in] Une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="bd7c9-108">[out] Une mémoire tampon qui contient le message d’erreur en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="bd7c9-109">[in] La taille de la mémoire tampon de message.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="bd7c9-110">[in] Ignoré.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd7c9-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bd7c9-111">Return Value</span></span>  
 <span data-ttu-id="bd7c9-112">Cette méthode retourne des codes d’erreur de composant COM (Object Model) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="bd7c9-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="bd7c9-113">Return code</span></span>|<span data-ttu-id="bd7c9-114">Description</span><span class="sxs-lookup"><span data-stu-id="bd7c9-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bd7c9-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd7c9-115">S_OK</span></span>|<span data-ttu-id="bd7c9-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="bd7c9-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bd7c9-117">E_INVALIDARG</span></span>|<span data-ttu-id="bd7c9-118">`szBuffer` a la valeur null ou `iMax` est zéro (0).</span><span class="sxs-lookup"><span data-stu-id="bd7c9-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd7c9-119">Notes</span><span class="sxs-lookup"><span data-stu-id="bd7c9-119">Remarks</span></span>  
 <span data-ttu-id="bd7c9-120">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd7c9-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd7c9-121">Requirements</span></span>  
 <span data-ttu-id="bd7c9-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd7c9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd7c9-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd7c9-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd7c9-124">**Bibliothèque :** MSCorEE.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="bd7c9-125">Utilisez MSCorEE.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd7c9-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="bd7c9-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd7c9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7c9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd7c9-127">See also</span></span>

- [<span data-ttu-id="bd7c9-128">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="bd7c9-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="bd7c9-129">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="bd7c9-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
