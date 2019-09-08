---
title: ImportFileEx2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776981"
---
# <a name="importfileex2-method"></a><span data-ttu-id="c9b05-102">ImportFileEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="c9b05-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="c9b05-103">Importe les assemblys et les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="c9b05-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="c9b05-104">Cette méthode est semblable à la [méthode ImportFile](importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="c9b05-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b05-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9b05-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9b05-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9b05-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c9b05-107">Nom du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="c9b05-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="c9b05-108">Nom facultatif du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="c9b05-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="c9b05-109">Option de l’interface de l’interface [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) facultative.</span><span class="sxs-lookup"><span data-stu-id="c9b05-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="c9b05-110">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="c9b05-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c9b05-111">Indicateurs à passer à la [méthode OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9b05-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="c9b05-112">Reçoit l’ID unique de l’assembly ou du fichier.</span><span class="sxs-lookup"><span data-stu-id="c9b05-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="c9b05-113">Reçoit l’interface de l’interface d’importation d’assembly [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b05-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="c9b05-114">Peut avoir la valeur NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="c9b05-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="c9b05-115">Reçoit le nombre de fichiers et/ou d’étendues importés.</span><span class="sxs-lookup"><span data-stu-id="c9b05-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9b05-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9b05-116">Return Value</span></span>  
 <span data-ttu-id="c9b05-117">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c9b05-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b05-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c9b05-118">Requirements</span></span>  
 <span data-ttu-id="c9b05-119">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c9b05-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b05-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9b05-120">See also</span></span>

- [<span data-ttu-id="c9b05-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c9b05-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c9b05-122">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c9b05-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c9b05-123">API ALink</span><span class="sxs-lookup"><span data-stu-id="c9b05-123">ALink API</span></span>](index.md)
