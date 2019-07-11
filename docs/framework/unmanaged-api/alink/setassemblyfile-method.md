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
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741535"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="13321-102">SetAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="13321-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="13321-103">Attribue le nom de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="13321-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="13321-104">Non pour être utilisés lors de la production de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="13321-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13321-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13321-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="13321-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13321-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="13321-107">Nom qualifié complet du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="13321-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="13321-108">Pointeur vers [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="13321-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="13321-109">Indicateurs tel que défini dans [AssemblyFlags, énumération](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="13321-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="13321-110">Pointeur vers l’ID de l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="13321-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13321-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="13321-111">Return Value</span></span>  
 <span data-ttu-id="13321-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="13321-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13321-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13321-113">Requirements</span></span>  
 <span data-ttu-id="13321-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="13321-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13321-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13321-115">See also</span></span>

- [<span data-ttu-id="13321-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="13321-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="13321-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="13321-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="13321-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="13321-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
