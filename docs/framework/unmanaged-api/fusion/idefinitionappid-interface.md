---
title: IDefinitionAppId, interface
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796510"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="18750-102">IDefinitionAppId, interface</span><span class="sxs-lookup"><span data-stu-id="18750-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="18750-103">Représente un identificateur unique pour le code qui définit l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="18750-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18750-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="18750-104">Methods</span></span>  
  
|<span data-ttu-id="18750-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="18750-105">Method</span></span>|<span data-ttu-id="18750-106">Description</span><span class="sxs-lookup"><span data-stu-id="18750-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="18750-107">Obtient une chaîne mise en forme qui représente le code `IDefinitionAppId` de cet objet.</span><span class="sxs-lookup"><span data-stu-id="18750-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="18750-108">Définit le code de cet `IDefinitionAppId` objet à la valeur de chaîne mise en forme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="18750-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="18750-109">Obtient un pointeur d’interface vers un objet [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) qui contient les assemblys dans le chemin d’accès de l’application actuelle.</span><span class="sxs-lookup"><span data-stu-id="18750-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="18750-110">Définit le chemin d’accès de l’application de l’assembly dans la portée actuelle à la valeur référencée par l’objet [IDefinitionIdentity](idefinitionidentity-interface.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="18750-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="18750-111">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un `IDefinitionAppId` abonnement à cet objet.</span><span class="sxs-lookup"><span data-stu-id="18750-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="18750-112">Définit l’identificateur de jeton pour un abonnement à cet `IDefinitionAppId` objet à la valeur de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="18750-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18750-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18750-113">Requirements</span></span>  
 <span data-ttu-id="18750-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18750-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18750-115">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="18750-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="18750-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18750-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18750-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18750-117">See also</span></span>

- [<span data-ttu-id="18750-118">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="18750-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
