---
title: CorLinkerOptions, énumération
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: fe5ffbab93df7168015e2a31d6e32ec45dce0960
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007687"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="6ec69-102">CorLinkerOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="6ec69-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="6ec69-103">Spécifie des indicateurs permettant de sélectionner des options pour l'éditeur de liens de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6ec69-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ec69-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="6ec69-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6ec69-105">Members</span></span>  
  
|<span data-ttu-id="6ec69-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6ec69-106">Member</span></span>|<span data-ttu-id="6ec69-107">Description</span><span class="sxs-lookup"><span data-stu-id="6ec69-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="6ec69-108">Les types privés et les fonctions globales ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="6ec69-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="6ec69-109">Les types privés et les fonctions globales sont conservés.</span><span class="sxs-lookup"><span data-stu-id="6ec69-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ec69-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ec69-110">Requirements</span></span>  
 <span data-ttu-id="6ec69-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec69-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec69-112">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="6ec69-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6ec69-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec69-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec69-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ec69-114">See also</span></span>

- [<span data-ttu-id="6ec69-115">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6ec69-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
