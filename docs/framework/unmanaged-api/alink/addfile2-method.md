---
title: AddFile2, méthode
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446668"
---
# <a name="addfile2-method"></a><span data-ttu-id="90ea5-102">AddFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="90ea5-102">AddFile2 Method</span></span>
<span data-ttu-id="90ea5-103">Adds files to the assembly.</span><span class="sxs-lookup"><span data-stu-id="90ea5-103">Adds files to the assembly.</span></span> <span data-ttu-id="90ea5-104">Can also be used to create unbound modules.</span><span class="sxs-lookup"><span data-stu-id="90ea5-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ea5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ea5-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="90ea5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90ea5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="90ea5-107">ID for the assembly to which the file is added.</span><span class="sxs-lookup"><span data-stu-id="90ea5-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="90ea5-108">Name of the file to be added.</span><span class="sxs-lookup"><span data-stu-id="90ea5-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="90ea5-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="90ea5-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="90ea5-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="90ea5-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="90ea5-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="90ea5-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="90ea5-112">Receives ID for the file being added.</span><span class="sxs-lookup"><span data-stu-id="90ea5-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90ea5-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90ea5-113">Return Value</span></span>  
 <span data-ttu-id="90ea5-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="90ea5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ea5-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="90ea5-115">Requirements</span></span>  
 <span data-ttu-id="90ea5-116">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="90ea5-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ea5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90ea5-117">See also</span></span>

- [<span data-ttu-id="90ea5-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="90ea5-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="90ea5-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="90ea5-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="90ea5-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="90ea5-120">ALink API</span></span>](index.md)
