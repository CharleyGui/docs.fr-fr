---
title: CorFileMapping, énumération
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726114"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="2339a-102">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="2339a-102">CorFileMapping Enumeration</span></span>

<span data-ttu-id="2339a-103">Contient des valeurs qui décrivent le type de mappage de fichier retourné à partir d’un appel à la méthode [IMetaDataInfo :: GetFileMapping,](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2339a-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2339a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2339a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="2339a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2339a-105">Members</span></span>  
  
|<span data-ttu-id="2339a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2339a-106">Member</span></span>|<span data-ttu-id="2339a-107">Description</span><span class="sxs-lookup"><span data-stu-id="2339a-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="2339a-108">Le fichier est mappé en tant que fichier de données.</span><span class="sxs-lookup"><span data-stu-id="2339a-108">The file is mapped as a data file.</span></span> <span data-ttu-id="2339a-109">Autrement dit, l' `SEC_IMAGE` indicateur n’a pas été passé à la `CreateFileMapping` fonction Microsoft Win32.</span><span class="sxs-lookup"><span data-stu-id="2339a-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="2339a-110">Le fichier est mappé pour exécution, à l’aide de la `LoadLibrary` fonction ou de la `CreateFileMapping` fonction avec l' `SEC_IMAGE` indicateur.</span><span class="sxs-lookup"><span data-stu-id="2339a-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2339a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2339a-111">Requirements</span></span>  

 <span data-ttu-id="2339a-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2339a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2339a-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="2339a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2339a-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2339a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2339a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2339a-115">See also</span></span>

- [<span data-ttu-id="2339a-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="2339a-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="2339a-117">GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="2339a-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
