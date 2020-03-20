---
title: _CorValidateImage, fonction
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178216"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="3c34b-102">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="3c34b-102">_CorValidateImage Function</span></span>
<span data-ttu-id="3c34b-103">Valide les images gérées du module et avise le chargeur du système d’exploitation après qu’ils ont été chargés.</span><span class="sxs-lookup"><span data-stu-id="3c34b-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c34b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c34b-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c34b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c34b-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="3c34b-106">[dans] Un pointeur vers l’emplacement de départ de l’image à valider en tant que code géré.</span><span class="sxs-lookup"><span data-stu-id="3c34b-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="3c34b-107">L’image doit déjà être chargée dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="3c34b-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="3c34b-108">[dans] Le nom du fichier de l’image.</span><span class="sxs-lookup"><span data-stu-id="3c34b-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c34b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3c34b-109">Return Value</span></span>  
 <span data-ttu-id="3c34b-110">Cette fonction retourne `E_INVALIDARG`les `E_OUTOFMEMORY` `E_UNEXPECTED`valeurs `E_FAIL`standard , , et , ainsi que les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="3c34b-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="3c34b-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3c34b-111">Return value</span></span>|<span data-ttu-id="3c34b-112">Description</span><span class="sxs-lookup"><span data-stu-id="3c34b-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="3c34b-113">L’image est invalide.</span><span class="sxs-lookup"><span data-stu-id="3c34b-113">The image is invalid.</span></span> <span data-ttu-id="3c34b-114">Cette valeur a le HRESULT 0xC00007BL.</span><span class="sxs-lookup"><span data-stu-id="3c34b-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="3c34b-115">L’image est valide.</span><span class="sxs-lookup"><span data-stu-id="3c34b-115">The image is valid.</span></span> <span data-ttu-id="3c34b-116">Cette valeur a le HRESULT 0x0000000L.</span><span class="sxs-lookup"><span data-stu-id="3c34b-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c34b-117">Notes </span><span class="sxs-lookup"><span data-stu-id="3c34b-117">Remarks</span></span>  
 <span data-ttu-id="3c34b-118">Dans Windows XP et les versions ultérieures, le chargeur de système d’exploitation vérifie les modules gérés en examinant le bit d’annuaire COM Descriptor dans l’en-tête du format de fichier objet commun (COFF).</span><span class="sxs-lookup"><span data-stu-id="3c34b-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="3c34b-119">Un bit défini indique un module géré.</span><span class="sxs-lookup"><span data-stu-id="3c34b-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="3c34b-120">Si le chargeur détecte un module géré, il charge MsCorEE.dll et appelle `_CorValidateImage`, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c34b-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="3c34b-121">Confirme que l’image est un module géré valide.</span><span class="sxs-lookup"><span data-stu-id="3c34b-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="3c34b-122">Modifie le point d’entrée de l’image à un point d’entrée dans l’heure de l’exécution de la langue commune (CLR).</span><span class="sxs-lookup"><span data-stu-id="3c34b-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="3c34b-123">Pour les versions 64 bits de Windows, modifie l’image qui est en mémoire en la transformant du format PE32 au format PE32.</span><span class="sxs-lookup"><span data-stu-id="3c34b-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="3c34b-124">Retourne à la chargeuse lorsque les images du module géré sont chargées.</span><span class="sxs-lookup"><span data-stu-id="3c34b-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="3c34b-125">Pour les images exécutables, le chargeur du système d’exploitation appelle alors la fonction [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) quel que soit le point d’entrée spécifié dans l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="3c34b-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="3c34b-126">Pour les images d’assemblage DLL, le chargeur appelle la [fonction _CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)</span><span class="sxs-lookup"><span data-stu-id="3c34b-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="3c34b-127">`_CorExeMain`ou `_CorDllMain` effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c34b-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="3c34b-128">Initialise le CLR.</span><span class="sxs-lookup"><span data-stu-id="3c34b-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="3c34b-129">Localise le point d’entrée géré à partir de l’en-tête CLR de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="3c34b-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="3c34b-130">Commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c34b-130">Begins execution.</span></span>  
  
 <span data-ttu-id="3c34b-131">Le chargeur appelle la fonction [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) lorsque les images du module gérée sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="3c34b-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="3c34b-132">Toutefois, cette fonction n’effectue aucune action; il revient juste.</span><span class="sxs-lookup"><span data-stu-id="3c34b-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c34b-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3c34b-133">Requirements</span></span>  
 <span data-ttu-id="3c34b-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c34b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c34b-135">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="3c34b-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c34b-136">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c34b-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c34b-137">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c34b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c34b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c34b-138">See also</span></span>

- [<span data-ttu-id="3c34b-139">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="3c34b-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
