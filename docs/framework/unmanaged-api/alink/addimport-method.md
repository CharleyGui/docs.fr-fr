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
ms.openlocfilehash: cf73ada36be66edb3fa267d61873ae9acb088a34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717043"
---
# <a name="addimport-method"></a><span data-ttu-id="59957-102">AddImport, méthode</span><span class="sxs-lookup"><span data-stu-id="59957-102">AddImport Method</span></span>

<span data-ttu-id="59957-103">Ajoute des importations à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="59957-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59957-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59957-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="59957-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59957-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="59957-106">ID unique de l’assembly à augmenter.</span><span class="sxs-lookup"><span data-stu-id="59957-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="59957-107">ID unique, récupéré à partir de la [méthode ImportFile](importfile-method.md), du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="59957-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="59957-108">Indicateurs FileDef COM+ tels que `ffContainsNoMetaData` et `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="59957-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="59957-109">`dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="59957-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="59957-110">Pointeur vers le jeton qui reçoit l’ID du fichier résultant.</span><span class="sxs-lookup"><span data-stu-id="59957-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59957-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="59957-111">Return Value</span></span>  

 <span data-ttu-id="59957-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="59957-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59957-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59957-113">Requirements</span></span>  

 <span data-ttu-id="59957-114">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="59957-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59957-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59957-115">See also</span></span>

- [<span data-ttu-id="59957-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="59957-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="59957-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="59957-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="59957-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="59957-118">ALink API</span></span>](index.md)
