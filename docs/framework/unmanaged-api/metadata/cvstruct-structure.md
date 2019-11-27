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
# <a name="cvstruct-structure"></a><span data-ttu-id="5ebbd-102">CVStruct, structure</span><span class="sxs-lookup"><span data-stu-id="5ebbd-102">CVStruct Structure</span></span>
<span data-ttu-id="5ebbd-103">Contient des informations utilisées lors de l'installation d'un module ou d'une image composite.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ebbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ebbd-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="5ebbd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5ebbd-105">Members</span></span>  
  
|<span data-ttu-id="5ebbd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5ebbd-106">Member</span></span>|<span data-ttu-id="5ebbd-107">Description</span><span class="sxs-lookup"><span data-stu-id="5ebbd-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5ebbd-108">Majeure</span><span class="sxs-lookup"><span data-stu-id="5ebbd-108">Major</span></span>|<span data-ttu-id="5ebbd-109">Numéro de build de la version principale.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-109">Major version build number.</span></span>|  
|<span data-ttu-id="5ebbd-110">Mineure</span><span class="sxs-lookup"><span data-stu-id="5ebbd-110">Minor</span></span>|<span data-ttu-id="5ebbd-111">Numéro de build de la version mineure.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-111">Minor version build number.</span></span>|  
|<span data-ttu-id="5ebbd-112">Sub</span><span class="sxs-lookup"><span data-stu-id="5ebbd-112">Sub</span></span>|<span data-ttu-id="5ebbd-113">Numéro de sous-Build.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-113">Sub-build number.</span></span>|  
|<span data-ttu-id="5ebbd-114">Build</span><span class="sxs-lookup"><span data-stu-id="5ebbd-114">Build</span></span>|<span data-ttu-id="5ebbd-115">Numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ebbd-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ebbd-116">Requirements</span></span>  
 <span data-ttu-id="5ebbd-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ebbd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ebbd-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ebbd-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ebbd-119">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ebbd-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ebbd-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ebbd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebbd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ebbd-121">See also</span></span>

- [<span data-ttu-id="5ebbd-122">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5ebbd-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
