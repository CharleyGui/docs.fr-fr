---
title: AddImport, méthode
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787664"
---
# <a name="addimport-method"></a><span data-ttu-id="f4082-102">AddImport, méthode</span><span class="sxs-lookup"><span data-stu-id="f4082-102">AddImport Method</span></span>
<span data-ttu-id="f4082-103">Ajoute des importations à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f4082-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4082-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4082-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4082-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4082-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f4082-106">ID unique de l’assembly à augmenter.</span><span class="sxs-lookup"><span data-stu-id="f4082-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="f4082-107">ID unique, récupéré à partir de la [méthode ImportFile](importfile-method.md), du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="f4082-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f4082-108">Indicateurs FileDef com+ tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="f4082-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="f4082-109">`dwFlags`est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f4082-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="f4082-110">Pointeur vers le jeton qui reçoit l’ID du fichier résultant.</span><span class="sxs-lookup"><span data-stu-id="f4082-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4082-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f4082-111">Return Value</span></span>  
 <span data-ttu-id="f4082-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="f4082-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4082-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f4082-113">Requirements</span></span>  
 <span data-ttu-id="f4082-114">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="f4082-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4082-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4082-115">See also</span></span>

- [<span data-ttu-id="f4082-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f4082-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f4082-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f4082-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f4082-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="f4082-118">ALink API</span></span>](index.md)
