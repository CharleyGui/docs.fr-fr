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
ms.openlocfilehash: 70d789f417700734b546cac6ff527ed5aa84fcf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688625"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="a26e2-102">CorFileFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="a26e2-102">CorFileFlags Enumeration</span></span>

<span data-ttu-id="a26e2-103">Contient des valeurs qui décrivent le type de fichier défini dans un appel à [IMetaDataAssemblyEmit ::D efinefile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a26e2-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a26e2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a26e2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a26e2-105">Members</span></span>  
  
|<span data-ttu-id="a26e2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a26e2-106">Member</span></span>|<span data-ttu-id="a26e2-107">Description</span><span class="sxs-lookup"><span data-stu-id="a26e2-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="a26e2-108">Indique que le fichier n’est pas un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="a26e2-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="a26e2-109">Indique que le fichier, éventuellement un fichier de ressources, ne contient pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a26e2-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a26e2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a26e2-110">Requirements</span></span>  

 <span data-ttu-id="a26e2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a26e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26e2-112">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a26e2-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a26e2-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26e2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a26e2-114">See also</span></span>

- [<span data-ttu-id="a26e2-115">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a26e2-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
