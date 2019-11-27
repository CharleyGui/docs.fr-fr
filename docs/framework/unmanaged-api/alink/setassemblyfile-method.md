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
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445606"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="0af2c-102">SetAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="0af2c-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="0af2c-103">Assigne le nom de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="0af2c-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="0af2c-104">Non utilisé lors de la génération de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="0af2c-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af2c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0af2c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0af2c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0af2c-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0af2c-107">Nom qualifié complet du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="0af2c-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="0af2c-108">Pointeur vers l’interface d' [interface d’IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0af2c-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="0af2c-109">Indicateurs tels que définis dans l' [énumération AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0af2c-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="0af2c-110">Pointeur vers l’ID de l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="0af2c-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0af2c-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0af2c-111">Return Value</span></span>  
 <span data-ttu-id="0af2c-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="0af2c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af2c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0af2c-113">Requirements</span></span>  
 <span data-ttu-id="0af2c-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="0af2c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af2c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0af2c-115">See also</span></span>

- [<span data-ttu-id="0af2c-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="0af2c-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0af2c-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="0af2c-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0af2c-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="0af2c-118">ALink API</span></span>](index.md)
