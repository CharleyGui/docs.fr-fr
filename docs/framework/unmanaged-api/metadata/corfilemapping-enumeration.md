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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007388"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="71ccf-102">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="71ccf-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="71ccf-103">Contient des valeurs qui décrivent le type de mappage de fichier retourné à partir d’un appel à la méthode [IMetaDataInfo :: GetFileMapping,](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="71ccf-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ccf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71ccf-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="71ccf-105">Membres</span><span class="sxs-lookup"><span data-stu-id="71ccf-105">Members</span></span>  
  
|<span data-ttu-id="71ccf-106">Membre</span><span class="sxs-lookup"><span data-stu-id="71ccf-106">Member</span></span>|<span data-ttu-id="71ccf-107">Description</span><span class="sxs-lookup"><span data-stu-id="71ccf-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="71ccf-108">Le fichier est mappé en tant que fichier de données.</span><span class="sxs-lookup"><span data-stu-id="71ccf-108">The file is mapped as a data file.</span></span> <span data-ttu-id="71ccf-109">Autrement dit, l' `SEC_IMAGE` indicateur n’a pas été passé à la `CreateFileMapping` fonction Microsoft Win32.</span><span class="sxs-lookup"><span data-stu-id="71ccf-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="71ccf-110">Le fichier est mappé pour exécution, à l’aide de la `LoadLibrary` fonction ou de la `CreateFileMapping` fonction avec l' `SEC_IMAGE` indicateur.</span><span class="sxs-lookup"><span data-stu-id="71ccf-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71ccf-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="71ccf-111">Requirements</span></span>  
 <span data-ttu-id="71ccf-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71ccf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ccf-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="71ccf-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="71ccf-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ccf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ccf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71ccf-115">See also</span></span>

- [<span data-ttu-id="71ccf-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="71ccf-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="71ccf-117">GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="71ccf-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
