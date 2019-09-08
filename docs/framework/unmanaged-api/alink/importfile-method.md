---
title: ImportFile, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7fee7a91de99e2db69609cbc7c73e22d85d045f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777060"
---
# <a name="importfile-method"></a><span data-ttu-id="e540a-102">ImportFile, méthode</span><span class="sxs-lookup"><span data-stu-id="e540a-102">ImportFile Method</span></span>
<span data-ttu-id="e540a-103">Importe les assemblys et les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="e540a-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e540a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e540a-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e540a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e540a-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e540a-106">Nom complet du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="e540a-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="e540a-107">Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier, car il est lié à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e540a-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="e540a-108">Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="e540a-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="e540a-109">Pointeur vers le jeton dans lequel un ID de fichier unique sera stocké.</span><span class="sxs-lookup"><span data-stu-id="e540a-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="e540a-110">Le fichier peut être un assembly ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="e540a-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="e540a-111">Reçoit un pointeur vers l' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e540a-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="e540a-112">Peut avoir la valeur NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="e540a-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="e540a-113">Pointeur vers le nombre de fichiers et/ou de portées qui ont été importés.</span><span class="sxs-lookup"><span data-stu-id="e540a-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e540a-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e540a-114">Return Value</span></span>  
 <span data-ttu-id="e540a-115">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="e540a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e540a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e540a-116">Requirements</span></span>  
 <span data-ttu-id="e540a-117">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="e540a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e540a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e540a-118">See also</span></span>

- [<span data-ttu-id="e540a-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e540a-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e540a-120">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e540a-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e540a-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="e540a-121">ALink API</span></span>](index.md)
