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
ms.openlocfilehash: da4b1d6f2a7079ef33859fce29c9555ac06fcfc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725649"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="508f6-102">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="508f6-102">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="508f6-103">Contient des informations sur les attributs de métadonnées concernant une instance de [IDefinitionIdentity](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="508f6-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="508f6-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="508f6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="508f6-105">Members</span></span>  
  
|<span data-ttu-id="508f6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="508f6-106">Member</span></span>|<span data-ttu-id="508f6-107">Description</span><span class="sxs-lookup"><span data-stu-id="508f6-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="508f6-108">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient l’espace de noms dans lequel se trouve l’attribut.</span><span class="sxs-lookup"><span data-stu-id="508f6-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="508f6-109">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="508f6-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="508f6-110">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="508f6-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="508f6-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="508f6-111">Remarks</span></span>  

 <span data-ttu-id="508f6-112">La `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères se terminant par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="508f6-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="508f6-113">Ces trois chaînes décrivent un attribut.</span><span class="sxs-lookup"><span data-stu-id="508f6-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="508f6-114">Une instance d’une `IDENTITY_ATTRIBUTE` structure est associée à une instance d’une structure [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="508f6-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="508f6-115">La `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et la structure correspondante `IDENTITY_ATTRIBUTE_BLOB` répertorie les offsets aux trois chaînes répertoriées dans la `IDENTITY_ATTRIBUTE` structure.</span><span class="sxs-lookup"><span data-stu-id="508f6-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508f6-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="508f6-116">Requirements</span></span>  

 <span data-ttu-id="508f6-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508f6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508f6-118">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="508f6-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="508f6-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508f6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508f6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="508f6-120">See also</span></span>

- [<span data-ttu-id="508f6-121">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="508f6-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="508f6-122">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="508f6-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="508f6-123">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="508f6-123">Fusion Structures</span></span>](fusion-structures.md)
