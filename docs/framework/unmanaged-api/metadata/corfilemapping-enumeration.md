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
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450295"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="c35c0-102">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="c35c0-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="c35c0-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="c35c0-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c35c0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="c35c0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c35c0-105">Members</span></span>  
  
|<span data-ttu-id="c35c0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c35c0-106">Member</span></span>|<span data-ttu-id="c35c0-107">Description</span><span class="sxs-lookup"><span data-stu-id="c35c0-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="c35c0-108">The file is mapped as a data file.</span><span class="sxs-lookup"><span data-stu-id="c35c0-108">The file is mapped as a data file.</span></span> <span data-ttu-id="c35c0-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span><span class="sxs-lookup"><span data-stu-id="c35c0-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="c35c0-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span><span class="sxs-lookup"><span data-stu-id="c35c0-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c35c0-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="c35c0-111">Requirements</span></span>  
 <span data-ttu-id="c35c0-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c35c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c35c0-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c35c0-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c35c0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c35c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35c0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c35c0-115">See also</span></span>

- [<span data-ttu-id="c35c0-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c35c0-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="c35c0-117">GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="c35c0-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
