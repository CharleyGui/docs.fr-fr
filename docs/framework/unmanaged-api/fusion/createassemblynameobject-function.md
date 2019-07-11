---
title: CreateAssemblyNameObject, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed26df6580aeaf2936bd50c9f1855a08ac68b90b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778434"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="24383-102">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="24383-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="24383-103">Obtient un pointeur d’interface vers un [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance qui représente l’identité unique de l’assembly avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="24383-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24383-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24383-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="24383-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24383-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="24383-106">[out] Retourné `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="24383-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="24383-107">[in] Le nom de l’assembly pour lequel créer le nouveau `IAssemblyName` instance.</span><span class="sxs-lookup"><span data-stu-id="24383-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="24383-108">[in] Indicateurs à passer au constructeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="24383-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="24383-109">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="24383-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="24383-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="24383-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24383-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24383-111">Requirements</span></span>  
 <span data-ttu-id="24383-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24383-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24383-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="24383-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="24383-114">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24383-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24383-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24383-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24383-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24383-116">See also</span></span>

- [<span data-ttu-id="24383-117">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="24383-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="24383-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="24383-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
