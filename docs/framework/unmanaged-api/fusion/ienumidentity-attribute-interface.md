---
title: IEnumIDENTITY_ATTRIBUTE, interface
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: 7e6bc57fb470a5c12549bb5f9445ecf1551425a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107840"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="bc34f-102">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="bc34f-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="bc34f-103">Sert d’énumérateur pour les attributs de l’objet de code dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="bc34f-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc34f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bc34f-104">Methods</span></span>  
  
|<span data-ttu-id="bc34f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bc34f-105">Method</span></span>|<span data-ttu-id="bc34f-106">Description</span><span class="sxs-lookup"><span data-stu-id="bc34f-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="bc34f-107">Obtient un pointeur d’interface vers un nouveau `IEnumIDENTITY_ATTRIBUTE` qui contient les mêmes membres que ce `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bc34f-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="bc34f-108">Écrit les données contenues dans les éléments de ce `IEnumIDENTITY_ATTRIBUTE` dans la mémoire tampon de données spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bc34f-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="bc34f-109">Obtient le nombre d’attributs spécifié, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="bc34f-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="bc34f-110">Déplace le pointeur d’instruction au début de cette `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bc34f-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="bc34f-111">Déplace le pointeur d’instruction vers l’avant par le nombre d’éléments spécifié, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="bc34f-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc34f-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="bc34f-112">Requirements</span></span>  
 <span data-ttu-id="bc34f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc34f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc34f-114">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="bc34f-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bc34f-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc34f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc34f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc34f-116">See also</span></span>

- [<span data-ttu-id="bc34f-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="bc34f-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
