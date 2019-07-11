---
title: CorImportOptions, énumération
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38c0937804eb82d1c96a605b55a00784ba58fe13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781828"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="70681-102">CorImportOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="70681-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="70681-103">Contient des valeurs d'indicateur qui contrôlent le comportement lors de l'importation d'un assembly en dehors de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="70681-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70681-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70681-104">Syntax</span></span>  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="70681-105">Membres</span><span class="sxs-lookup"><span data-stu-id="70681-105">Members</span></span>  
  
|<span data-ttu-id="70681-106">Membre</span><span class="sxs-lookup"><span data-stu-id="70681-106">Member</span></span>|<span data-ttu-id="70681-107">Description</span><span class="sxs-lookup"><span data-stu-id="70681-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="70681-108">Indique le comportement par défaut, qui consiste à ignorer les enregistrements supprimés.</span><span class="sxs-lookup"><span data-stu-id="70681-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="70681-109">Indique que toutes les métadonnées doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="70681-110">Indique que tous les TypeDefs, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="70681-111">Indique que tous les MethodDefs, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="70681-112">Indique que tous les FieldDefs, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="70681-113">Indique que tous les PropertyDefs, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="70681-114">Indique que tous les EventDefs, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="70681-115">Indique que tous les attributs personnalisés, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="70681-116">Indique que tous les types exportés, y compris ceux qui sont supprimés, doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="70681-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70681-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="70681-117">Requirements</span></span>  
 <span data-ttu-id="70681-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70681-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70681-119">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="70681-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="70681-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70681-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70681-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70681-121">See also</span></span>

- [<span data-ttu-id="70681-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="70681-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
