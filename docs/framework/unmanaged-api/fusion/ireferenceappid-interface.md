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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131660"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="052f4-102">IReferenceAppId, interface</span><span class="sxs-lookup"><span data-stu-id="052f4-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="052f4-103">Représente une référence à l’identificateur unique de l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="052f4-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="052f4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="052f4-104">Methods</span></span>  
  
|<span data-ttu-id="052f4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="052f4-105">Method</span></span>|<span data-ttu-id="052f4-106">Description</span><span class="sxs-lookup"><span data-stu-id="052f4-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="052f4-107">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de code pour l’application référencée par cet `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="052f4-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="052f4-108">Définit l’identificateur de code pour l’application référencée par cette `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="052f4-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="052f4-109">Obtient un pointeur d’interface vers une instance de `IEnumReferenceIdentity` contenant les instances `IReferenceIdentity` qui représentent les membres de ce `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="052f4-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="052f4-110">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à cette `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="052f4-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="052f4-111">Définit l’identificateur de jeton pour un abonnement à cet `IReferenceAppId` à la valeur de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="052f4-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="052f4-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="052f4-112">Requirements</span></span>  
 <span data-ttu-id="052f4-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="052f4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="052f4-114">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="052f4-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="052f4-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="052f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052f4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="052f4-116">See also</span></span>

- [<span data-ttu-id="052f4-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="052f4-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="052f4-118">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="052f4-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="052f4-119">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="052f4-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
