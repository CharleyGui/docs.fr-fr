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
ms.openlocfilehash: e6584d31674670bcd005161a846b74df71a27a5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741650"
---
# <a name="importfileex2-method"></a><span data-ttu-id="03695-102">ImportFileEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="03695-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="03695-103">Importe des assemblys et modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="03695-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="03695-104">Cette méthode est comparable à [ImportFile, méthode](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="03695-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03695-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03695-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="03695-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="03695-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="03695-107">Nom du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="03695-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="03695-108">Nom facultatif du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="03695-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="03695-109">Portée d’importation facultative [IMetaDataAssemblyImport, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="03695-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="03695-110">Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="03695-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="03695-111">Indicateurs à passer à [OpenScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="03695-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="03695-112">Reçoit l’ID unique du fichier ou l’assembly.</span><span class="sxs-lookup"><span data-stu-id="03695-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="03695-113">Reçoit la portée d’importation assembly [IMetaDataAssemblyImport, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="03695-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="03695-114">Peut être NULL si le fichier n'est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="03695-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="03695-115">Reçoit le nombre de fichiers et/ou de portées importés.</span><span class="sxs-lookup"><span data-stu-id="03695-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03695-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="03695-116">Return Value</span></span>  
 <span data-ttu-id="03695-117">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="03695-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03695-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="03695-118">Requirements</span></span>  
 <span data-ttu-id="03695-119">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="03695-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03695-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03695-120">See also</span></span>

- [<span data-ttu-id="03695-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="03695-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="03695-122">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="03695-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="03695-123">API ALink</span><span class="sxs-lookup"><span data-stu-id="03695-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
