---
title: GetHistoryFileDirectory, fonction
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724436"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="4c6a7-102">GetHistoryFileDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="4c6a7-102">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="4c6a7-103">Récupère le chemin d’accès du répertoire de l’historique de l’application.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c6a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c6a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c6a7-105">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="4c6a7-106">à Mémoire tampon pour stocker le chemin d’accès au répertoire de l’historique de l’application.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="4c6a7-107">[in, out] Longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c6a7-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="4c6a7-108">Return Value</span></span>  

 <span data-ttu-id="4c6a7-109">Cette méthode retourne les codes d’erreur COM standard, tels que définis dans le fichier WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="4c6a7-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="4c6a7-110">Return code</span></span>|<span data-ttu-id="4c6a7-111">Description</span><span class="sxs-lookup"><span data-stu-id="4c6a7-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4c6a7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c6a7-112">S_OK</span></span>|<span data-ttu-id="4c6a7-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4c6a7-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4c6a7-114">E_INVALIDARG</span></span>|<span data-ttu-id="4c6a7-115">`wzDir` ou `pdwSize` est null, ou la chaîne de version est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c6a7-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="4c6a7-116">Remarks</span></span>  

 <span data-ttu-id="4c6a7-117">Une fois l’opération terminée, l' `pdwSize` argument est défini sur la longueur de la chaîne de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c6a7-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4c6a7-118">Requirements</span></span>  

 <span data-ttu-id="4c6a7-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c6a7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c6a7-120">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4c6a7-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4c6a7-121">**Bibliothèque :** Fusion.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="4c6a7-122">Utilisez Fusion.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c6a7-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4c6a7-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c6a7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c6a7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c6a7-124">See also</span></span>

- [<span data-ttu-id="4c6a7-125">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="4c6a7-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="4c6a7-126">NukeDownloadedCache, fonction</span><span class="sxs-lookup"><span data-stu-id="4c6a7-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="4c6a7-127">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="4c6a7-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
