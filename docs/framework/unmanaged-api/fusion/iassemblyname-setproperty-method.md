---
title: IAssemblyName::SetProperty, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: ffa1fa2f5e141728a56f1b598a1aae9602b2ac86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108221"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="25f07-102">IAssemblyName::SetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="25f07-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="25f07-103">Définit la valeur de la propriété référencée par l’identificateur de propriété spécifié.</span><span class="sxs-lookup"><span data-stu-id="25f07-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f07-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25f07-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25f07-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="25f07-106">dans Identificateur unique de la propriété dont la valeur sera définie.</span><span class="sxs-lookup"><span data-stu-id="25f07-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="25f07-107">dans Valeur à laquelle définir la propriété référencée par `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="25f07-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="25f07-108">dans Taille, en octets, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="25f07-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f07-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="25f07-109">Requirements</span></span>  
 <span data-ttu-id="25f07-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f07-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f07-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="25f07-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="25f07-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f07-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25f07-113">See also</span></span>

- [<span data-ttu-id="25f07-114">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="25f07-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
