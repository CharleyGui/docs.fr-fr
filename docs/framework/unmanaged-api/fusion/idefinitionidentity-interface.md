---
title: IDefinitionIdentity, interface
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 4f08fbbf9c8be16dff092327713e731c5aa14661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732868"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="43e9d-102">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="43e9d-102">IDefinitionIdentity Interface</span></span>

<span data-ttu-id="43e9d-103">Représente la signature unique du code qui définit l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="43e9d-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43e9d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43e9d-104">Methods</span></span>  
  
|<span data-ttu-id="43e9d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="43e9d-105">Method</span></span>|<span data-ttu-id="43e9d-106">Description</span><span class="sxs-lookup"><span data-stu-id="43e9d-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="43e9d-107">Obtient un pointeur d’interface vers un nouvel `IDefinitionIdentity` objet qui est identique à celui-ci `IDefinitionIdentity` , à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="43e9d-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="43e9d-108">Obtient un pointeur d’interface vers un objet [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) qui contient les attributs associés à ce `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="43e9d-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="43e9d-109">Obtient la valeur de l’attribut avec le nom spécifié dans l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="43e9d-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="43e9d-110">Affecte la valeur spécifiée à l’attribut qui porte le nom spécifié dans l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="43e9d-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43e9d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="43e9d-111">Requirements</span></span>  

 <span data-ttu-id="43e9d-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43e9d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e9d-113">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="43e9d-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="43e9d-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43e9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e9d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43e9d-115">See also</span></span>

- [<span data-ttu-id="43e9d-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="43e9d-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
