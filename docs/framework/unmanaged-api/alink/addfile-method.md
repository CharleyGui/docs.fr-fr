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
# <a name="addfile-method"></a><span data-ttu-id="3532b-102">AddFile, méthode</span><span class="sxs-lookup"><span data-stu-id="3532b-102">AddFile Method</span></span>
<span data-ttu-id="3532b-103">Ajoute des fichiers à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3532b-103">Adds files to the assembly.</span></span> <span data-ttu-id="3532b-104">Peut également être utilisé pour créer des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="3532b-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3532b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3532b-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3532b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3532b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3532b-107">ID unique de l’assembly à augmenter.</span><span class="sxs-lookup"><span data-stu-id="3532b-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="3532b-108">Nom complet du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="3532b-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3532b-109">Indicateurs FileDef COM+, tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="3532b-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="3532b-110">`dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="3532b-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="3532b-111">Interface d' [interface d’IMetaDataEmit](../metadata/imetadataemit-interface.md) à utiliser pour émettre des métadonnées, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3532b-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="3532b-112">Pointeur vers l’emplacement où l’ID unique du fichier ajouté sera stocké.</span><span class="sxs-lookup"><span data-stu-id="3532b-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3532b-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3532b-113">Return Value</span></span>  
 <span data-ttu-id="3532b-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="3532b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3532b-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3532b-115">Requirements</span></span>  
 <span data-ttu-id="3532b-116">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="3532b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3532b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3532b-117">See also</span></span>

- [<span data-ttu-id="3532b-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="3532b-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3532b-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="3532b-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3532b-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="3532b-120">ALink API</span></span>](index.md)
