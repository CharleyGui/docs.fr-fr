---
title: IEnumDefinitionIdentity, interface
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbd8476b7778de6d0023f3a8522a44be6626884
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751529"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="75483-102">IEnumDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="75483-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="75483-103">Sert d’énumérateur pour une collection de `IDefinitionIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="75483-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75483-104">Syntax</span></span>  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="75483-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="75483-105">Methods</span></span>  
  
|<span data-ttu-id="75483-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="75483-106">Method</span></span>|<span data-ttu-id="75483-107">Description</span><span class="sxs-lookup"><span data-stu-id="75483-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="75483-108">Obtient un pointeur d’interface vers un nouveau `IEnumDefinitionIdentity` objet qui contient les mêmes membres que cela `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="75483-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="75483-109">Obtient le nombre spécifié de `IDefinitionIdentity` objets, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="75483-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="75483-110">Déplace le pointeur d’instruction au début de ce `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="75483-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="75483-111">Déplace le pointeur d’instruction par le nombre spécifié d’éléments, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="75483-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75483-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75483-112">Requirements</span></span>  
 <span data-ttu-id="75483-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75483-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75483-114">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="75483-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="75483-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75483-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75483-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75483-116">See also</span></span>

- [<span data-ttu-id="75483-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="75483-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="75483-118">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="75483-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
