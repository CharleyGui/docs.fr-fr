---
title: ImportFile2, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446986"
---
# <a name="importfile2-method"></a><span data-ttu-id="21b34-102">ImportFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="21b34-102">ImportFile2 Method</span></span>
<span data-ttu-id="21b34-103">Imports assemblies and unbound modules.</span><span class="sxs-lookup"><span data-stu-id="21b34-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="21b34-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span><span class="sxs-lookup"><span data-stu-id="21b34-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b34-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b34-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="21b34-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21b34-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="21b34-107">Name of file to be imported.</span><span class="sxs-lookup"><span data-stu-id="21b34-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="21b34-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span><span class="sxs-lookup"><span data-stu-id="21b34-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="21b34-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="21b34-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="21b34-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span><span class="sxs-lookup"><span data-stu-id="21b34-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="21b34-111">Receives the ID for the file or assembly.</span><span class="sxs-lookup"><span data-stu-id="21b34-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="21b34-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="21b34-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="21b34-113">NULL if the file is not an assembly.</span><span class="sxs-lookup"><span data-stu-id="21b34-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="21b34-114">Receives the found of files and/or scopes imported.</span><span class="sxs-lookup"><span data-stu-id="21b34-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b34-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21b34-115">Return Value</span></span>  
 <span data-ttu-id="21b34-116">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="21b34-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b34-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="21b34-117">Requirements</span></span>  
 <span data-ttu-id="21b34-118">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="21b34-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b34-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21b34-119">See also</span></span>

- [<span data-ttu-id="21b34-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="21b34-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21b34-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="21b34-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21b34-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="21b34-122">ALink API</span></span>](index.md)
