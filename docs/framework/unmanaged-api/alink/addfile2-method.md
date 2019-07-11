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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de85d264d709da747fab636f40c99bc0d0752251
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742358"
---
# <a name="addfile2-method"></a><span data-ttu-id="c6607-102">AddFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="c6607-102">AddFile2 Method</span></span>
<span data-ttu-id="c6607-103">Ajoute des fichiers à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c6607-103">Adds files to the assembly.</span></span> <span data-ttu-id="c6607-104">Peut également être utilisé pour créer des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="c6607-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6607-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6607-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6607-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6607-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c6607-107">ID de l’assembly auquel le fichier est ajouté.</span><span class="sxs-lookup"><span data-stu-id="c6607-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c6607-108">Nom du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="c6607-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c6607-109">COM + `FileDef` indicateurs tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="c6607-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c6607-110">`dwFlags` est passé à [DefineFile, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6607-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c6607-111">Interface à [IMetaDataEmit2, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="c6607-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c6607-112">Reçoit l’ID du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="c6607-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6607-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6607-113">Return Value</span></span>  
 <span data-ttu-id="c6607-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="c6607-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6607-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6607-115">Requirements</span></span>  
 <span data-ttu-id="c6607-116">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="c6607-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6607-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6607-117">See also</span></span>

- [<span data-ttu-id="c6607-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c6607-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c6607-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c6607-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c6607-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="c6607-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
