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
ms.openlocfilehash: 1193af7b7375dfd3367c12fdb0067c9c30c614f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741751"
---
# <a name="importfile2-method"></a><span data-ttu-id="f7340-102">ImportFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="f7340-102">ImportFile2 Method</span></span>
<span data-ttu-id="f7340-103">Importe des assemblys et modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="f7340-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="f7340-104">Cette méthode est comparable à [ImportFile, méthode](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="f7340-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7340-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7340-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f7340-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7340-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="f7340-107">Nom du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="f7340-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="f7340-108">Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier car il est lié dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f7340-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="f7340-109">Portée facultative [IMetaDataAssemblyImport, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f7340-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="f7340-110">Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="f7340-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="f7340-111">Reçoit l’ID pour le fichier ou l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f7340-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="f7340-112">Reçoit le [IMetaDataAssemblyImport, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f7340-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="f7340-113">NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="f7340-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="f7340-114">Reçoit le trouvé de fichiers et/ou de portées importés.</span><span class="sxs-lookup"><span data-stu-id="f7340-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7340-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7340-115">Return Value</span></span>  
 <span data-ttu-id="f7340-116">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f7340-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7340-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7340-117">Requirements</span></span>  
 <span data-ttu-id="f7340-118">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="f7340-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7340-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7340-119">See also</span></span>

- [<span data-ttu-id="f7340-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f7340-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f7340-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f7340-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f7340-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="f7340-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
