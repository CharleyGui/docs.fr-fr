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
ms.openlocfilehash: 2657ac619bb86bc200de9ce229bf82e4339f78d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796297"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="4f4af-102">GetAssemblyIdentityFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="4f4af-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="4f4af-103">Obtient un pointeur vers un `IUnknown` objet avec le spécifié `IID` dans l’assembly dans le chemin d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="4f4af-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f4af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f4af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f4af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f4af-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="4f4af-106">dans Chemin d’accès valide à l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="4f4af-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="4f4af-107">dans `IID` De l’interface à retourner.</span><span class="sxs-lookup"><span data-stu-id="4f4af-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="4f4af-108">à Pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="4f4af-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f4af-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4f4af-109">Requirements</span></span>  
 <span data-ttu-id="4f4af-110">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f4af-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f4af-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4f4af-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4f4af-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f4af-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f4af-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f4af-113">See also</span></span>

- [<span data-ttu-id="4f4af-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="4f4af-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="4f4af-115">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="4f4af-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
