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
ms.openlocfilehash: d02bc53676dd5afb0222a1ea366a8f2bd1f94f62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705226"
---
# <a name="importfile2-method"></a><span data-ttu-id="ec141-102">ImportFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="ec141-102">ImportFile2 Method</span></span>

<span data-ttu-id="ec141-103">Importe les assemblys et les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="ec141-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="ec141-104">Cette méthode est semblable à la [méthode ImportFile](importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="ec141-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec141-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec141-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ec141-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec141-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="ec141-107">Nom du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="ec141-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="ec141-108">Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier, car il est lié à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ec141-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="ec141-109">Portée facultative, interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ec141-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="ec141-110">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="ec141-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="ec141-111">Reçoit l’ID du fichier ou de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ec141-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="ec141-112">Reçoit l’interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ec141-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="ec141-113">NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="ec141-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="ec141-114">Reçoit le trouvé des fichiers et/ou des étendues importés.</span><span class="sxs-lookup"><span data-stu-id="ec141-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec141-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ec141-115">Return Value</span></span>  

 <span data-ttu-id="ec141-116">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="ec141-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec141-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec141-117">Requirements</span></span>  

 <span data-ttu-id="ec141-118">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="ec141-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec141-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec141-119">See also</span></span>

- [<span data-ttu-id="ec141-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="ec141-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ec141-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="ec141-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ec141-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="ec141-122">ALink API</span></span>](index.md)
