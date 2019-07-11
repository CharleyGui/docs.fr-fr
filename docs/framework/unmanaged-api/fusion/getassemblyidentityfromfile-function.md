---
title: GetAssemblyIdentityFromFile, fonction
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581c675cfb69503e6366471a469ffed1a2d13b1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745227"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="44a22-102">GetAssemblyIdentityFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="44a22-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="44a22-103">Obtient un pointeur vers un `IUnknown` objet avec la valeur `IID` dans l’assembly dans le chemin de fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="44a22-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="44a22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44a22-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="44a22-106">[in] Un chemin d’accès valide à l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="44a22-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="44a22-107">[in] Le `IID` de l’interface à retourner.</span><span class="sxs-lookup"><span data-stu-id="44a22-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="44a22-108">[out] Le pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="44a22-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44a22-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="44a22-109">Requirements</span></span>  
 <span data-ttu-id="44a22-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44a22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44a22-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="44a22-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="44a22-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44a22-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a22-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44a22-113">See also</span></span>

- [<span data-ttu-id="44a22-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="44a22-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="44a22-115">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="44a22-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
