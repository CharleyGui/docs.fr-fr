---
title: IReferenceIdentity, interface
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 867c09caa3bd3aed50de21c2ef91a02782830be2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704550"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="81774-102">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="81774-102">IReferenceIdentity Interface</span></span>

<span data-ttu-id="81774-103">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="81774-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81774-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="81774-104">Methods</span></span>  
  
|<span data-ttu-id="81774-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="81774-105">Method</span></span>|<span data-ttu-id="81774-106">Description</span><span class="sxs-lookup"><span data-stu-id="81774-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="81774-107">Obtient un pointeur d’interface vers une nouvelle `IReferenceIdentity` instance qui est identique à celle-ci `IReferenceIdentity` , à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="81774-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="81774-108">Obtient un pointeur d’interface vers une `IEnumIDENTITY_ATTRIBUTE` instance de qui contient les attributs associés à ce `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="81774-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="81774-109">Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="81774-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="81774-110">Définit l’attribut qui a l’espace de noms spécifié et le nom spécifié sur la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="81774-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81774-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81774-111">Requirements</span></span>  

 <span data-ttu-id="81774-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81774-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81774-113">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="81774-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="81774-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81774-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81774-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81774-115">See also</span></span>

- [<span data-ttu-id="81774-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="81774-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="81774-117">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="81774-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
