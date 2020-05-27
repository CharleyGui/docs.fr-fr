---
title: CorPEKind, énumération
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007557"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="e25d7-102">CorPEKind, énumération</span><span class="sxs-lookup"><span data-stu-id="e25d7-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="e25d7-103">Contient des valeurs qui décrivent un fichier exécutable portable (PE, Portable Executable), tel qu’il est retourné à partir d’un appel à [IMetaDataImport2 :: GetPEKind,](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="e25d7-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e25d7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="e25d7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e25d7-105">Members</span></span>  
  
|<span data-ttu-id="e25d7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e25d7-106">Member</span></span>|<span data-ttu-id="e25d7-107">Description</span><span class="sxs-lookup"><span data-stu-id="e25d7-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="e25d7-108">Indique qu’il ne s’agit pas d’un fichier PE.</span><span class="sxs-lookup"><span data-stu-id="e25d7-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="e25d7-109">Indique que ce fichier PE contient uniquement du code managé.</span><span class="sxs-lookup"><span data-stu-id="e25d7-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="e25d7-110">Indique que ce fichier PE effectue des appels Win32.</span><span class="sxs-lookup"><span data-stu-id="e25d7-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="e25d7-111">Indique que ce fichier PE s’exécute sur une plateforme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e25d7-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="e25d7-112">Indique que ce fichier PE est du code natif.</span><span class="sxs-lookup"><span data-stu-id="e25d7-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="e25d7-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="e25d7-113">pe32BitPreferred</span></span>|<span data-ttu-id="e25d7-114">Indique que ce fichier PE est indépendant de la plateforme et qu’il préfère être chargé dans un environnement 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e25d7-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e25d7-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="e25d7-115">Remarks</span></span>  
 <span data-ttu-id="e25d7-116">Ces valeurs peuvent être utilisées dans des combinaisons au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="e25d7-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25d7-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e25d7-117">Requirements</span></span>  
 <span data-ttu-id="e25d7-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e25d7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25d7-119">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e25d7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e25d7-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e25d7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25d7-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e25d7-121">See also</span></span>

- [<span data-ttu-id="e25d7-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e25d7-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
