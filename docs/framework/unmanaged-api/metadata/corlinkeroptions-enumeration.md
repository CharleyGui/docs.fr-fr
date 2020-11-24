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
ms.openlocfilehash: 188301d31b2fcfaf7b1c6139111e8f1296ccf7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677242"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="7e68c-102">CorLinkerOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="7e68c-102">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="7e68c-103">Spécifie des indicateurs permettant de sélectionner des options pour l'éditeur de liens de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7e68c-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e68c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e68c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="7e68c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7e68c-105">Members</span></span>  
  
|<span data-ttu-id="7e68c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7e68c-106">Member</span></span>|<span data-ttu-id="7e68c-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e68c-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="7e68c-108">Les types privés et les fonctions globales ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="7e68c-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="7e68c-109">Les types privés et les fonctions globales sont conservés.</span><span class="sxs-lookup"><span data-stu-id="7e68c-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e68c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e68c-110">Requirements</span></span>  

 <span data-ttu-id="7e68c-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e68c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e68c-112">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7e68c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7e68c-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e68c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e68c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e68c-114">See also</span></span>

- [<span data-ttu-id="7e68c-115">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="7e68c-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
