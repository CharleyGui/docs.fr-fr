---
title: CorSaveSize, énumération
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 0f870d9d7d1bc292b213d690df508a6c28bac2ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450102"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="5faf4-102">CorSaveSize, énumération</span><span class="sxs-lookup"><span data-stu-id="5faf4-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="5faf4-103">Contient des valeurs indiquant le niveau de précision requis lors de l'interrogation de la taille d'une opération d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="5faf4-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5faf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5faf4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="5faf4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5faf4-105">Members</span></span>  
  
|<span data-ttu-id="5faf4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5faf4-106">Member</span></span>|<span data-ttu-id="5faf4-107">Description</span><span class="sxs-lookup"><span data-stu-id="5faf4-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="5faf4-108">Spécifie que la valeur de retour doit être exacte.</span><span class="sxs-lookup"><span data-stu-id="5faf4-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="5faf4-109">Spécifie que la valeur de retour doit être estimée.</span><span class="sxs-lookup"><span data-stu-id="5faf4-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="5faf4-110">Spécifie que les types pouvant être éliminés doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="5faf4-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5faf4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5faf4-111">Requirements</span></span>  
 <span data-ttu-id="5faf4-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5faf4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5faf4-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5faf4-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5faf4-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5faf4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5faf4-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5faf4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faf4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5faf4-116">See also</span></span>

- [<span data-ttu-id="5faf4-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5faf4-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
