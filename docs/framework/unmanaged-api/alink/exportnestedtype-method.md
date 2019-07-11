---
title: ExportNestedType, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfaedad48291ac09f6959bc7b314ae0d9da76e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742042"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="f9540-102">ExportNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="f9540-102">ExportNestedType Method</span></span>
<span data-ttu-id="f9540-103">Spécifie les types imbriqués comme étant exportables.</span><span class="sxs-lookup"><span data-stu-id="f9540-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="f9540-104">Le [ExportType, méthode](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) peut également exporter les types imbriqués, mais cette méthode est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="f9540-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9540-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9540-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="f9540-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9540-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f9540-107">ID de l’assembly à exporter à partir de.</span><span class="sxs-lookup"><span data-stu-id="f9540-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f9540-108">Jeton de fichier ou l’Assembly du fichier qui définit le type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="f9540-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="f9540-109">Type de jeton de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="f9540-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="f9540-110">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="f9540-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f9540-111">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="f9540-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f9540-112">`ComType` indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f9540-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="f9540-113">Cette valeur peut être passée à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f9540-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="f9540-114">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="f9540-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9540-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f9540-115">Return Value</span></span>  
 <span data-ttu-id="f9540-116">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f9540-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9540-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9540-117">Requirements</span></span>  
 <span data-ttu-id="f9540-118">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="f9540-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9540-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9540-119">See also</span></span>

- [<span data-ttu-id="f9540-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f9540-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f9540-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f9540-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f9540-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="f9540-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
