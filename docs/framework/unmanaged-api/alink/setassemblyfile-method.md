---
title: SetAssemblyFile, méthode
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777002"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="7d337-102">SetAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="7d337-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="7d337-103">Assigne le nom de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="7d337-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="7d337-104">Non utilisé lors de la génération de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="7d337-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d337-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d337-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d337-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d337-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7d337-107">Nom qualifié complet du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="7d337-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="7d337-108">Pointeur vers l’interface d' [interface d’IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d337-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="7d337-109">Indicateurs tels que définis dans l' [énumération AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7d337-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="7d337-110">Pointeur vers l’ID de l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="7d337-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d337-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7d337-111">Return Value</span></span>  
 <span data-ttu-id="7d337-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="7d337-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d337-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7d337-113">Requirements</span></span>  
 <span data-ttu-id="7d337-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="7d337-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d337-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d337-115">See also</span></span>

- [<span data-ttu-id="7d337-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="7d337-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7d337-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="7d337-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7d337-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="7d337-118">ALink API</span></span>](index.md)
