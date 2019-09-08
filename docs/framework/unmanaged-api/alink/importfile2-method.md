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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776937"
---
# <a name="importfile2-method"></a><span data-ttu-id="118f2-102">ImportFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="118f2-102">ImportFile2 Method</span></span>
<span data-ttu-id="118f2-103">Importe les assemblys et les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="118f2-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="118f2-104">Cette méthode est semblable à la [méthode ImportFile](importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="118f2-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="118f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="118f2-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="118f2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="118f2-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="118f2-107">Nom du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="118f2-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="118f2-108">Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier, car il est lié à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="118f2-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="118f2-109">Portée facultative, interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="118f2-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="118f2-110">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="118f2-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="118f2-111">Reçoit l’ID du fichier ou de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="118f2-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="118f2-112">Reçoit l’interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="118f2-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="118f2-113">NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="118f2-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="118f2-114">Reçoit le trouvé des fichiers et/ou des étendues importés.</span><span class="sxs-lookup"><span data-stu-id="118f2-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="118f2-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="118f2-115">Return Value</span></span>  
 <span data-ttu-id="118f2-116">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="118f2-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="118f2-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="118f2-117">Requirements</span></span>  
 <span data-ttu-id="118f2-118">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="118f2-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118f2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="118f2-119">See also</span></span>

- [<span data-ttu-id="118f2-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="118f2-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="118f2-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="118f2-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="118f2-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="118f2-122">ALink API</span></span>](index.md)
