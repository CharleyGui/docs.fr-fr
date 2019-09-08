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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796357"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="79b86-102">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="79b86-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="79b86-103">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="79b86-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79b86-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="79b86-104">Methods</span></span>  
  
|<span data-ttu-id="79b86-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="79b86-105">Method</span></span>|<span data-ttu-id="79b86-106">Description</span><span class="sxs-lookup"><span data-stu-id="79b86-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="79b86-107">Obtient un pointeur d’interface vers une `IReferenceIdentity` nouvelle instance qui est identique à `IReferenceIdentity`celle-ci, à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="79b86-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="79b86-108">Obtient un pointeur d’interface vers `IEnumIDENTITY_ATTRIBUTE` une instance de qui contient les attributs associés `IReferenceIdentity`à ce.</span><span class="sxs-lookup"><span data-stu-id="79b86-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="79b86-109">Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="79b86-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="79b86-110">Définit l’attribut qui a l’espace de noms spécifié et le nom spécifié sur la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="79b86-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79b86-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79b86-111">Requirements</span></span>  
 <span data-ttu-id="79b86-112">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b86-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b86-113">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="79b86-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="79b86-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b86-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79b86-115">See also</span></span>

- [<span data-ttu-id="79b86-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="79b86-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="79b86-117">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="79b86-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
