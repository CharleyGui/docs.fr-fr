---
title: ImportFileEx, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: 9e373f133830a5bc1f3cf7bdc8034cb67725d797
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705200"
---
# <a name="importfileex-method"></a><span data-ttu-id="82e11-102">ImportFileEx, méthode</span><span class="sxs-lookup"><span data-stu-id="82e11-102">ImportFileEx Method</span></span>

<span data-ttu-id="82e11-103">Importe l’assembly ou le module indépendant indiqué.</span><span class="sxs-lookup"><span data-stu-id="82e11-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e11-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e11-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82e11-105">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="82e11-106">Nom complet du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="82e11-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="82e11-107">Nom facultatif du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="82e11-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="82e11-108">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="82e11-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="82e11-109">Indicateurs à passer à la [méthode OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="82e11-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="82e11-110">Reçoit l’ID du fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="82e11-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="82e11-111">Reçoit l’interface de l’interface d’importation d’assembly [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="82e11-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="82e11-112">A la valeur NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="82e11-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="82e11-113">Reçoit le nombre de fichiers et/ou d’étendues importés.</span><span class="sxs-lookup"><span data-stu-id="82e11-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e11-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="82e11-114">Return Value</span></span>  

 <span data-ttu-id="82e11-115">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="82e11-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e11-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82e11-116">Requirements</span></span>  

 <span data-ttu-id="82e11-117">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="82e11-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e11-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82e11-118">See also</span></span>

- [<span data-ttu-id="82e11-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="82e11-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="82e11-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="82e11-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="82e11-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="82e11-121">ALink API</span></span>](index.md)
