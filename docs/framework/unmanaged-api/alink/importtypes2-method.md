---
title: ImportTypes2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: 8dae903ab76ab83ac0818c4bc4a76e81094bdf65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445666"
---
# <a name="importtypes2-method"></a><span data-ttu-id="55c15-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="55c15-102">ImportTypes2 Method</span></span>
<span data-ttu-id="55c15-103">Initiates the import of types.</span><span class="sxs-lookup"><span data-stu-id="55c15-103">Initiates the import of types.</span></span> <span data-ttu-id="55c15-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="55c15-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c15-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55c15-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="55c15-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55c15-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="55c15-107">ID of assembly into which to import.</span><span class="sxs-lookup"><span data-stu-id="55c15-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="55c15-108">ID of file to from which to import.</span><span class="sxs-lookup"><span data-stu-id="55c15-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="55c15-109">Zero-based scope from which to import.</span><span class="sxs-lookup"><span data-stu-id="55c15-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="55c15-110">Receives enumerator handle for the types in the given scope.</span><span class="sxs-lookup"><span data-stu-id="55c15-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="55c15-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="55c15-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="55c15-112">Optionally receives count of types in the specified scope.</span><span class="sxs-lookup"><span data-stu-id="55c15-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55c15-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="55c15-113">Return Value</span></span>  
 <span data-ttu-id="55c15-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="55c15-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c15-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="55c15-115">Requirements</span></span>  
 <span data-ttu-id="55c15-116">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="55c15-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c15-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c15-117">See also</span></span>

- [<span data-ttu-id="55c15-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="55c15-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="55c15-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="55c15-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="55c15-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="55c15-120">ALink API</span></span>](index.md)
