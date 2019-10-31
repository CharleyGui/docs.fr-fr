---
title: ICLRDebuggingLibraryProvider::ProvideLibrary, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 8fc2abd0728115edbbfae42958d8013029523ed1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111363"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="843ec-102">ICLRDebuggingLibraryProvider::ProvideLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="843ec-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="843ec-103">Obtient une interface de rappel de fournisseur de bibliothèque qui permet de localiser et de charger des bibliothèques de débogage spécifiques à la version common language runtime (CLR) à la demande.</span><span class="sxs-lookup"><span data-stu-id="843ec-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="843ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="843ec-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="843ec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="843ec-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="843ec-106">dans Nom du module demandé.</span><span class="sxs-lookup"><span data-stu-id="843ec-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="843ec-107">dans Horodatage stocké dans l’en-tête de fichier COFF des fichiers PE.</span><span class="sxs-lookup"><span data-stu-id="843ec-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="843ec-108">dans Champ `SizeOfImage` stocké dans l’en-tête de fichier facultatif COFF des fichiers PE.</span><span class="sxs-lookup"><span data-stu-id="843ec-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="843ec-109">à Handle du module demandé.</span><span class="sxs-lookup"><span data-stu-id="843ec-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="843ec-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="843ec-110">Return Value</span></span>

<span data-ttu-id="843ec-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="843ec-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="843ec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="843ec-112">HRESULT</span></span>|<span data-ttu-id="843ec-113">Description</span><span class="sxs-lookup"><span data-stu-id="843ec-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="843ec-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="843ec-114">S_OK</span></span>|<span data-ttu-id="843ec-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="843ec-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="843ec-116">Exceptions</span><span class="sxs-lookup"><span data-stu-id="843ec-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="843ec-117">Notes</span><span class="sxs-lookup"><span data-stu-id="843ec-117">Remarks</span></span>

<span data-ttu-id="843ec-118">`ProvideLibrary` permet au débogueur de fournir des modules nécessaires pour déboguer des fichiers CLR spécifiques tels que mscordbi. dll et mscordacwks. dll.</span><span class="sxs-lookup"><span data-stu-id="843ec-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="843ec-119">Les handles de module doivent rester valides jusqu’à ce qu’un appel à la méthode [ICLRDebugging :: CanUnloadNow,](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) indique qu’ils peuvent être libérés. à partir de là, il est de la responsabilité de l’appelant de libérer les handles.</span><span class="sxs-lookup"><span data-stu-id="843ec-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="843ec-120">Le débogueur peut utiliser n’importe quel moyen disponible pour rechercher ou acquérir le module de débogage.</span><span class="sxs-lookup"><span data-stu-id="843ec-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="843ec-121">Cette fonctionnalité permet à l’appelant de l’API de fournir des modules qui contiennent du code exécutable et éventuellement malveillant.</span><span class="sxs-lookup"><span data-stu-id="843ec-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="843ec-122">Par mesure de sécurité, l’appelant ne doit pas utiliser `ProvideLibrary` pour distribuer du code qu’il n’est pas disposé à s’exécuter lui-même.</span><span class="sxs-lookup"><span data-stu-id="843ec-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="843ec-123">Si un problème de sécurité sérieux est découvert dans une bibliothèque déjà publiée, telle que mscordbi. dll ou mscordacwks. dll, le shim peut être corrigé pour reconnaître les versions erronées des fichiers.</span><span class="sxs-lookup"><span data-stu-id="843ec-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="843ec-124">Le shim peut ensuite émettre des demandes pour les versions corrigées des fichiers et rejeter les versions erronées Si elles sont fournies en réponse à une demande.</span><span class="sxs-lookup"><span data-stu-id="843ec-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="843ec-125">Cela peut se produire uniquement si l’utilisateur a appliqué une nouvelle version du shim.</span><span class="sxs-lookup"><span data-stu-id="843ec-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="843ec-126">Les versions non corrigées resteront vulnérables.</span><span class="sxs-lookup"><span data-stu-id="843ec-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="843ec-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="843ec-127">Requirements</span></span>

<span data-ttu-id="843ec-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="843ec-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="843ec-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="843ec-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="843ec-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="843ec-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="843ec-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="843ec-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="843ec-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="843ec-132">See also</span></span>

- [<span data-ttu-id="843ec-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="843ec-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="843ec-134">Débogage</span><span class="sxs-lookup"><span data-stu-id="843ec-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
