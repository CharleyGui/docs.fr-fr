---
title: CVStruct, structure
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 19ee3097dfe80ba9dcbdaf316db0fd165b50abc6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436428"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="85d3c-102">CVStruct, structure</span><span class="sxs-lookup"><span data-stu-id="85d3c-102">CVStruct Structure</span></span>
<span data-ttu-id="85d3c-103">Contient des informations utilisées lors de l'installation d'un module ou d'une image composite.</span><span class="sxs-lookup"><span data-stu-id="85d3c-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85d3c-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="85d3c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="85d3c-105">Members</span></span>  
  
|<span data-ttu-id="85d3c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="85d3c-106">Member</span></span>|<span data-ttu-id="85d3c-107">Description</span><span class="sxs-lookup"><span data-stu-id="85d3c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="85d3c-108">Majeur</span><span class="sxs-lookup"><span data-stu-id="85d3c-108">Major</span></span>|<span data-ttu-id="85d3c-109">Major version build number.</span><span class="sxs-lookup"><span data-stu-id="85d3c-109">Major version build number.</span></span>|  
|<span data-ttu-id="85d3c-110">Mineur</span><span class="sxs-lookup"><span data-stu-id="85d3c-110">Minor</span></span>|<span data-ttu-id="85d3c-111">Minor version build number.</span><span class="sxs-lookup"><span data-stu-id="85d3c-111">Minor version build number.</span></span>|  
|<span data-ttu-id="85d3c-112">Sub</span><span class="sxs-lookup"><span data-stu-id="85d3c-112">Sub</span></span>|<span data-ttu-id="85d3c-113">Sub-build number.</span><span class="sxs-lookup"><span data-stu-id="85d3c-113">Sub-build number.</span></span>|  
|<span data-ttu-id="85d3c-114">Générer</span><span class="sxs-lookup"><span data-stu-id="85d3c-114">Build</span></span>|<span data-ttu-id="85d3c-115">Build number.</span><span class="sxs-lookup"><span data-stu-id="85d3c-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85d3c-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="85d3c-116">Requirements</span></span>  
 <span data-ttu-id="85d3c-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d3c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d3c-118">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85d3c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85d3c-119">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85d3c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85d3c-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d3c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d3c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85d3c-121">See also</span></span>

- [<span data-ttu-id="85d3c-122">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="85d3c-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
