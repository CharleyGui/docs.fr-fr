---
title: CorFileFlags, énumération
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: c8c2757e99b80204ad52e69a596d62c55c369965
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007414"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="eeeb3-102">CorFileFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="eeeb3-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="eeeb3-103">Contient des valeurs qui décrivent le type de fichier défini dans un appel à [IMetaDataAssemblyEmit ::D efinefile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="eeeb3-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeeb3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeeb3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="eeeb3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="eeeb3-105">Members</span></span>  
  
|<span data-ttu-id="eeeb3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="eeeb3-106">Member</span></span>|<span data-ttu-id="eeeb3-107">Description</span><span class="sxs-lookup"><span data-stu-id="eeeb3-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="eeeb3-108">Indique que le fichier n’est pas un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="eeeb3-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="eeeb3-109">Indique que le fichier, éventuellement un fichier de ressources, ne contient pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="eeeb3-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eeeb3-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eeeb3-110">Requirements</span></span>  
 <span data-ttu-id="eeeb3-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeeb3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeeb3-112">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="eeeb3-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eeeb3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeeb3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeeb3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeeb3-114">See also</span></span>

- [<span data-ttu-id="eeeb3-115">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="eeeb3-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
