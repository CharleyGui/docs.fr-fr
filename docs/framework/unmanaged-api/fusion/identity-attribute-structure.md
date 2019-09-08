---
title: IDENTITY_ATTRIBUTE, structure
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796482"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="9b2b1-102">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="9b2b1-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="9b2b1-103">Contient des informations sur les attributs de métadonnées concernant une instance de [IDefinitionIdentity](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b2b1-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b2b1-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="9b2b1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b2b1-105">Members</span></span>  
  
|<span data-ttu-id="9b2b1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b2b1-106">Member</span></span>|<span data-ttu-id="9b2b1-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b2b1-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="9b2b1-108">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient l’espace de noms dans lequel se trouve l’attribut.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="9b2b1-109">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="9b2b1-110">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b2b1-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9b2b1-111">Remarks</span></span>  
 <span data-ttu-id="9b2b1-112">La `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères se terminant par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="9b2b1-113">Ces trois chaînes décrivent un attribut.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="9b2b1-114">Une instance d’une `IDENTITY_ATTRIBUTE` structure est associée à une instance d’une structure [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="9b2b1-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="9b2b1-115">La `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et la structure correspondante `IDENTITY_ATTRIBUTE_BLOB` répertorie les offsets aux trois chaînes répertoriées dans la `IDENTITY_ATTRIBUTE` structure.</span><span class="sxs-lookup"><span data-stu-id="9b2b1-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2b1-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b2b1-116">Requirements</span></span>  
 <span data-ttu-id="9b2b1-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b2b1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b2b1-118">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="9b2b1-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9b2b1-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b2b1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b2b1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b2b1-120">See also</span></span>

- [<span data-ttu-id="9b2b1-121">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="9b2b1-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="9b2b1-122">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="9b2b1-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="9b2b1-123">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="9b2b1-123">Fusion Structures</span></span>](fusion-structures.md)
