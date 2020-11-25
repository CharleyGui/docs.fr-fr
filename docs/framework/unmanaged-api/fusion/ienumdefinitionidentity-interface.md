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
ms.openlocfilehash: f3872a2b03d3b22d695af1c104e9ae8ba8856990
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729003"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="1a70e-102">IEnumDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="1a70e-102">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="1a70e-103">Sert d’énumérateur pour une collection d' `IDefinitionIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="1a70e-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a70e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a70e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1a70e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1a70e-105">Methods</span></span>  
  
|<span data-ttu-id="1a70e-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="1a70e-106">Method</span></span>|<span data-ttu-id="1a70e-107">Description</span><span class="sxs-lookup"><span data-stu-id="1a70e-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="1a70e-108">Obtient un pointeur d’interface vers un nouvel `IEnumDefinitionIdentity` objet qui contient les mêmes membres que ce `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="1a70e-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="1a70e-109">Obtient le nombre spécifié d' `IDefinitionIdentity` objets, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="1a70e-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="1a70e-110">Déplace le pointeur d’instruction au début de ce `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="1a70e-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="1a70e-111">Déplace le pointeur d’instruction vers l’avant par le nombre d’éléments spécifié, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="1a70e-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a70e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a70e-112">Requirements</span></span>  

 <span data-ttu-id="1a70e-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a70e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a70e-114">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="1a70e-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1a70e-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a70e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a70e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a70e-116">See also</span></span>

- [<span data-ttu-id="1a70e-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="1a70e-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1a70e-118">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="1a70e-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
