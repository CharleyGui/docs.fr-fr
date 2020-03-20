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
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176238"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="165ff-102">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="165ff-102">LoadStringRC Function</span></span>
<span data-ttu-id="165ff-103">Traduit une valeur HRESULT en message d’erreur en utilisant la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="165ff-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="165ff-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="165ff-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="165ff-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="165ff-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="165ff-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="165ff-107">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="165ff-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="165ff-108">[out] Un tampon qui contient le message d’erreur une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="165ff-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="165ff-109">[dans] La taille du tampon de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="165ff-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="165ff-110">[dans] Ignoré.</span><span class="sxs-lookup"><span data-stu-id="165ff-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="165ff-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="165ff-111">Return Value</span></span>  
 <span data-ttu-id="165ff-112">Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="165ff-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="165ff-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="165ff-113">Return code</span></span>|<span data-ttu-id="165ff-114">Description</span><span class="sxs-lookup"><span data-stu-id="165ff-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="165ff-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="165ff-115">S_OK</span></span>|<span data-ttu-id="165ff-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="165ff-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="165ff-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="165ff-117">E_INVALIDARG</span></span>|<span data-ttu-id="165ff-118">`szBuffer`est nul `iMax` ou est nul (0).</span><span class="sxs-lookup"><span data-stu-id="165ff-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="165ff-119">Notes </span><span class="sxs-lookup"><span data-stu-id="165ff-119">Remarks</span></span>  
 <span data-ttu-id="165ff-120">Si la méthode ne `szBuffer` se termine pas avec succès, contient une ficelle vide.</span><span class="sxs-lookup"><span data-stu-id="165ff-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165ff-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="165ff-121">Requirements</span></span>  
 <span data-ttu-id="165ff-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="165ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="165ff-123">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="165ff-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="165ff-124">**Bibliothèque:** MSCorEE.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="165ff-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="165ff-125">Utilisez MSCorEE.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="165ff-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="165ff-126">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="165ff-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165ff-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="165ff-127">See also</span></span>

- [<span data-ttu-id="165ff-128">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="165ff-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="165ff-129">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="165ff-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
