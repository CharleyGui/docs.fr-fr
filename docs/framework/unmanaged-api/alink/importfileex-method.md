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
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446950"
---
# <a name="importfileex-method"></a><span data-ttu-id="e1210-102">ImportFileEx, méthode</span><span class="sxs-lookup"><span data-stu-id="e1210-102">ImportFileEx Method</span></span>
<span data-ttu-id="e1210-103">Importe l’assembly ou le module indépendant indiqué.</span><span class="sxs-lookup"><span data-stu-id="e1210-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1210-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1210-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e1210-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1210-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e1210-106">Nom complet du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="e1210-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="e1210-107">Nom facultatif du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="e1210-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="e1210-108">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="e1210-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e1210-109">Indicateurs à passer à la [méthode OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="e1210-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="e1210-110">Reçoit l’ID du fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="e1210-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="e1210-111">Reçoit l’interface de l’interface d’importation d’assembly [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e1210-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="e1210-112">A la valeur NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="e1210-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="e1210-113">Reçoit le nombre de fichiers et/ou d’étendues importés.</span><span class="sxs-lookup"><span data-stu-id="e1210-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1210-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e1210-114">Return Value</span></span>  
 <span data-ttu-id="e1210-115">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="e1210-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1210-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1210-116">Requirements</span></span>  
 <span data-ttu-id="e1210-117">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="e1210-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1210-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1210-118">See also</span></span>

- [<span data-ttu-id="e1210-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e1210-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e1210-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e1210-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e1210-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="e1210-121">ALink API</span></span>](index.md)
