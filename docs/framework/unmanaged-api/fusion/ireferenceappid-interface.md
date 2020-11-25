---
title: IReferenceAppId, interface
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728613"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="0e599-102">IReferenceAppId, interface</span><span class="sxs-lookup"><span data-stu-id="0e599-102">IReferenceAppId Interface</span></span>

<span data-ttu-id="0e599-103">Représente une référence à l’identificateur unique de l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="0e599-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e599-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0e599-104">Methods</span></span>  
  
|<span data-ttu-id="0e599-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0e599-105">Method</span></span>|<span data-ttu-id="0e599-106">Description</span><span class="sxs-lookup"><span data-stu-id="0e599-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="0e599-107">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de code pour l’application référencée par ce `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0e599-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="0e599-108">Définit l’identificateur de code pour l’application référencée par ce `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0e599-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="0e599-109">Obtient un pointeur d’interface vers une `IEnumReferenceIdentity` instance de contenant les `IReferenceIdentity` instances qui représentent les membres de ce `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0e599-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="0e599-110">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à ce `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0e599-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="0e599-111">Définit l’identificateur de jeton pour un abonnement à ce `IReferenceAppId` à la valeur de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0e599-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e599-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e599-112">Requirements</span></span>  

 <span data-ttu-id="0e599-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e599-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e599-114">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="0e599-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0e599-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e599-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e599-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e599-116">See also</span></span>

- [<span data-ttu-id="0e599-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="0e599-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="0e599-118">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="0e599-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="0e599-119">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="0e599-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
