---
title: EmbedResource, méthode
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446536"
---
# <a name="embedresource-method"></a><span data-ttu-id="9d351-102">EmbedResource, méthode</span><span class="sxs-lookup"><span data-stu-id="9d351-102">EmbedResource Method</span></span>
<span data-ttu-id="9d351-103">Déclare une ressource incorporée.</span><span class="sxs-lookup"><span data-stu-id="9d351-103">Declares an embedded resource.</span></span> <span data-ttu-id="9d351-104">Cette méthode n’incorpore pas réellement la ressource.</span><span class="sxs-lookup"><span data-stu-id="9d351-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d351-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d351-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d351-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d351-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9d351-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d351-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9d351-108">Jeton de fichier ou ID d’assembly du fichier qui contient la ressource.</span><span class="sxs-lookup"><span data-stu-id="9d351-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="9d351-109">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="9d351-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="9d351-110">Décalage de la ressource à partir de RVA.</span><span class="sxs-lookup"><span data-stu-id="9d351-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d351-111">Indicateurs d’accessibilité tels que `mrPublic` et `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="9d351-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="9d351-112">Ces indicateurs peuvent être passés à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d351-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d351-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d351-113">Return Value</span></span>  
 <span data-ttu-id="9d351-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="9d351-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d351-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d351-115">Requirements</span></span>  
 <span data-ttu-id="9d351-116">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="9d351-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d351-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d351-117">See also</span></span>

- [<span data-ttu-id="9d351-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="9d351-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9d351-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="9d351-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9d351-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="9d351-120">ALink API</span></span>](index.md)
