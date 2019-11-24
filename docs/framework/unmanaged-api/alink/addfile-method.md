---
title: AddFile, méthode
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446685"
---
# <a name="addfile-method"></a><span data-ttu-id="207d1-102">AddFile, méthode</span><span class="sxs-lookup"><span data-stu-id="207d1-102">AddFile Method</span></span>
<span data-ttu-id="207d1-103">Adds files to the assembly.</span><span class="sxs-lookup"><span data-stu-id="207d1-103">Adds files to the assembly.</span></span> <span data-ttu-id="207d1-104">Can also be used to create unbound modules.</span><span class="sxs-lookup"><span data-stu-id="207d1-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="207d1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="207d1-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="207d1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="207d1-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="207d1-107">Unique ID of the assembly to be augmented.</span><span class="sxs-lookup"><span data-stu-id="207d1-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="207d1-108">Fully qualified name of file to be added.</span><span class="sxs-lookup"><span data-stu-id="207d1-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="207d1-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="207d1-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="207d1-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="207d1-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="207d1-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span><span class="sxs-lookup"><span data-stu-id="207d1-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="207d1-112">Pointer to where the unique ID of the added file will be stored.</span><span class="sxs-lookup"><span data-stu-id="207d1-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="207d1-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="207d1-113">Return Value</span></span>  
 <span data-ttu-id="207d1-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="207d1-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="207d1-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="207d1-115">Requirements</span></span>  
 <span data-ttu-id="207d1-116">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="207d1-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207d1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="207d1-117">See also</span></span>

- [<span data-ttu-id="207d1-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="207d1-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="207d1-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="207d1-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="207d1-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="207d1-120">ALink API</span></span>](index.md)
