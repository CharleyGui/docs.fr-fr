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
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717082"
---
# <a name="addfile2-method"></a><span data-ttu-id="58248-102">AddFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="58248-102">AddFile2 Method</span></span>

<span data-ttu-id="58248-103">Ajoute des fichiers à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58248-103">Adds files to the assembly.</span></span> <span data-ttu-id="58248-104">Peut également être utilisé pour créer des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="58248-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58248-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58248-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="58248-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58248-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="58248-107">ID de l’assembly auquel le fichier est ajouté.</span><span class="sxs-lookup"><span data-stu-id="58248-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="58248-108">Nom du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="58248-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="58248-109">`FileDef`Indicateurs com+ tels que `ffContainsNoMetaData` et `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="58248-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="58248-110">`dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="58248-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="58248-111">Interface de l’interface de l' [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="58248-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="58248-112">Reçoit l’ID du fichier en cours d’ajout.</span><span class="sxs-lookup"><span data-stu-id="58248-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58248-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="58248-113">Return Value</span></span>  

 <span data-ttu-id="58248-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="58248-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58248-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58248-115">Requirements</span></span>  

 <span data-ttu-id="58248-116">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="58248-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58248-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58248-117">See also</span></span>

- [<span data-ttu-id="58248-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="58248-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="58248-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="58248-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="58248-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="58248-120">ALink API</span></span>](index.md)
