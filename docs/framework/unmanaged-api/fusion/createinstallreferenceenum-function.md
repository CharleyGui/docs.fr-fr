---
title: Fonction CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da77d2eb848419c35e57ffacc8bf3d4580106fa5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764323"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="0e5ff-102">Fonction CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="0e5ff-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="0e5ff-103">Obtient un pointeur vers un [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance qui représente une liste de références d’une application à l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e5ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e5ff-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e5ff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e5ff-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="0e5ff-106">[out] Retourné `IInstallReferenceEnum` pointeur.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="0e5ff-107">[in] Le [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) qui identifie l’assembly pour lequel énumérer des références.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0e5ff-108">[in] Indicateurs qui influencent le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="0e5ff-109">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="0e5ff-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e5ff-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e5ff-111">Requirements</span></span>  
 <span data-ttu-id="0e5ff-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e5ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e5ff-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0e5ff-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0e5ff-114">**Bibliothèque :** Le fichier fusion.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="0e5ff-115">Utilisez le fichier Fusion.dll plutôt que Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e5ff-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0e5ff-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e5ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5ff-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e5ff-117">See also</span></span>

- [<span data-ttu-id="0e5ff-118">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="0e5ff-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [<span data-ttu-id="0e5ff-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="0e5ff-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="0e5ff-120">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="0e5ff-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
