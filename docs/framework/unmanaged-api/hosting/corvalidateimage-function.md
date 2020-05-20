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
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616500"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="25787-102">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="25787-102">_CorValidateImage Function</span></span>
<span data-ttu-id="25787-103">Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="25787-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25787-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25787-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25787-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25787-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="25787-106">dans Pointeur vers l’emplacement de départ de l’image à valider comme code managé.</span><span class="sxs-lookup"><span data-stu-id="25787-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="25787-107">L’image doit déjà être chargée dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="25787-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="25787-108">dans Nom de fichier de l’image.</span><span class="sxs-lookup"><span data-stu-id="25787-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25787-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="25787-109">Return Value</span></span>  
 <span data-ttu-id="25787-110">Cette fonction retourne les valeurs standard `E_INVALIDARG` , `E_OUTOFMEMORY` , `E_UNEXPECTED` et `E_FAIL` , ainsi que les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="25787-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="25787-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="25787-111">Return value</span></span>|<span data-ttu-id="25787-112">Description</span><span class="sxs-lookup"><span data-stu-id="25787-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="25787-113">L’image n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="25787-113">The image is invalid.</span></span> <span data-ttu-id="25787-114">Cette valeur a le HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="25787-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="25787-115">L’image est valide.</span><span class="sxs-lookup"><span data-stu-id="25787-115">The image is valid.</span></span> <span data-ttu-id="25787-116">Cette valeur a le HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="25787-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25787-117">Notes</span><span class="sxs-lookup"><span data-stu-id="25787-117">Remarks</span></span>  
 <span data-ttu-id="25787-118">Dans Windows XP et versions ultérieures, le chargeur du système d’exploitation recherche les modules managés en examinant le bit du répertoire du descripteur COM dans l’en-tête COFF (Common Object File Format).</span><span class="sxs-lookup"><span data-stu-id="25787-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="25787-119">Un bit défini indique un module managé.</span><span class="sxs-lookup"><span data-stu-id="25787-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="25787-120">Si le chargeur détecte un module managé, il charge MsCorEE. dll et appelle `_CorValidateImage` , qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="25787-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="25787-121">Confirme que l’image est un module managé valide.</span><span class="sxs-lookup"><span data-stu-id="25787-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="25787-122">Modifie le point d’entrée dans l’image en point d’entrée dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="25787-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="25787-123">Pour les versions 64 bits de Windows, modifie l’image en mémoire en la transformant de PE32 en format PE32 +.</span><span class="sxs-lookup"><span data-stu-id="25787-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="25787-124">Retourne au chargeur lorsque les images de modules managés sont chargées.</span><span class="sxs-lookup"><span data-stu-id="25787-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="25787-125">Pour les images exécutables, le chargeur du système d’exploitation appelle ensuite la fonction [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) , quel que soit le point d’entrée spécifié dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="25787-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="25787-126">Pour les images d’assembly DLL, le chargeur appelle la fonction [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="25787-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="25787-127">`_CorExeMain`ou `_CorDllMain` effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="25787-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="25787-128">Initialise le CLR.</span><span class="sxs-lookup"><span data-stu-id="25787-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="25787-129">Localise le point d’entrée managé dans l’en-tête CLR de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="25787-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="25787-130">Commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="25787-130">Begins execution.</span></span>  
  
 <span data-ttu-id="25787-131">Le chargeur appelle la fonction [_CorImageUnloading](corimageunloading-function.md) lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="25787-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="25787-132">Toutefois, cette fonction n’exécute aucune action ; elle retourne simplement.</span><span class="sxs-lookup"><span data-stu-id="25787-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25787-133">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="25787-133">Requirements</span></span>  
 <span data-ttu-id="25787-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25787-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25787-135">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25787-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25787-136">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25787-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25787-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25787-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25787-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25787-138">See also</span></span>

- [<span data-ttu-id="25787-139">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="25787-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
