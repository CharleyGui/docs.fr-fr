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
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724479"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="72a6b-102">GetAssemblyIdentityFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="72a6b-102">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="72a6b-103">Obtient un pointeur vers un `IUnknown` objet avec le spécifié `IID` dans l’assembly dans le chemin d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="72a6b-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72a6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a6b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72a6b-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="72a6b-106">dans Chemin d’accès valide à l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="72a6b-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="72a6b-107">dans `IID` De l’interface à retourner.</span><span class="sxs-lookup"><span data-stu-id="72a6b-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="72a6b-108">à Pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="72a6b-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a6b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="72a6b-109">Requirements</span></span>  

 <span data-ttu-id="72a6b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a6b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a6b-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="72a6b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="72a6b-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a6b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a6b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a6b-113">See also</span></span>

- [<span data-ttu-id="72a6b-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="72a6b-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="72a6b-115">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="72a6b-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
