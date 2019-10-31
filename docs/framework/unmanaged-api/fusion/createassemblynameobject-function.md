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
ms.openlocfilehash: 00345f6c95c67f0494aa721c662f56a9e98cdd7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108711"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="cbbae-102">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="cbbae-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="cbbae-103">Obtient un pointeur d’interface vers une instance de [IAssemblyName](iassemblyname-interface.md) qui représente l’identité unique de l’assembly avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="cbbae-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbbae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbbae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbbae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbbae-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="cbbae-106">à `IAssemblyName`retourné.</span><span class="sxs-lookup"><span data-stu-id="cbbae-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="cbbae-107">dans Nom de l’assembly pour lequel la nouvelle instance de `IAssemblyName` doit être créée.</span><span class="sxs-lookup"><span data-stu-id="cbbae-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cbbae-108">dans Indicateurs à passer au constructeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="cbbae-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cbbae-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="cbbae-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cbbae-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="cbbae-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbbae-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="cbbae-111">Requirements</span></span>  
 <span data-ttu-id="cbbae-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbbae-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbbae-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cbbae-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cbbae-114">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbbae-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbbae-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbbae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbae-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbbae-116">See also</span></span>

- [<span data-ttu-id="cbbae-117">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="cbbae-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="cbbae-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="cbbae-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
