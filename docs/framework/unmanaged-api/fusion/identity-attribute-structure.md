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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107980"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="d035e-102">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="d035e-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="d035e-103">Contient des informations sur les attributs de métadonnées concernant une instance de [IDefinitionIdentity](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d035e-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d035e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d035e-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="d035e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d035e-105">Members</span></span>  
  
|<span data-ttu-id="d035e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d035e-106">Member</span></span>|<span data-ttu-id="d035e-107">Description</span><span class="sxs-lookup"><span data-stu-id="d035e-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="d035e-108">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient l’espace de noms dans lequel se trouve l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d035e-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="d035e-109">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d035e-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="d035e-110">Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d035e-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d035e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d035e-111">Remarks</span></span>  
 <span data-ttu-id="d035e-112">La structure `IDENTITY_ATTRIBUTE` contient trois pointeurs vers des chaînes de caractères se terminant par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="d035e-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="d035e-113">Ces trois chaînes décrivent un attribut.</span><span class="sxs-lookup"><span data-stu-id="d035e-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="d035e-114">Une instance d’une structure `IDENTITY_ATTRIBUTE` est associée à une instance d’une structure [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d035e-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="d035e-115">La structure `IDENTITY_ATTRIBUTE` contient les chaînes réelles, et la structure de `IDENTITY_ATTRIBUTE_BLOB` correspondante répertorie les offsets aux trois chaînes répertoriées dans la structure `IDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="d035e-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d035e-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="d035e-116">Requirements</span></span>  
 <span data-ttu-id="d035e-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d035e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d035e-118">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="d035e-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d035e-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d035e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d035e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d035e-120">See also</span></span>

- [<span data-ttu-id="d035e-121">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="d035e-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="d035e-122">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="d035e-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="d035e-123">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="d035e-123">Fusion Structures</span></span>](fusion-structures.md)
