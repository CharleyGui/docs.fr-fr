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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906b5ef2795d8fad996185f66f145a8cd3618c41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781807"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="cbcc6-102">CorLinkerOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="cbcc6-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="cbcc6-103">Spécifie des indicateurs permettant de sélectionner des options pour l'éditeur de liens de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cbcc6-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbcc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbcc6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="cbcc6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cbcc6-105">Members</span></span>  
  
|<span data-ttu-id="cbcc6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cbcc6-106">Member</span></span>|<span data-ttu-id="cbcc6-107">Description</span><span class="sxs-lookup"><span data-stu-id="cbcc6-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="cbcc6-108">Les types privés et les fonctions globales ne sont pas conservées.</span><span class="sxs-lookup"><span data-stu-id="cbcc6-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="cbcc6-109">Les types privés et les fonctions globales sont conservées.</span><span class="sxs-lookup"><span data-stu-id="cbcc6-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbcc6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cbcc6-110">Requirements</span></span>  
 <span data-ttu-id="cbcc6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbcc6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbcc6-112">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cbcc6-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cbcc6-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbcc6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbcc6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbcc6-114">See also</span></span>

- [<span data-ttu-id="cbcc6-115">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="cbcc6-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
