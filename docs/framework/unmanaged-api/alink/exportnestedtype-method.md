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
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777278"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="4d732-102">ExportNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="4d732-102">ExportNestedType Method</span></span>
<span data-ttu-id="4d732-103">Spécifie que les types imbriqués sont exportables.</span><span class="sxs-lookup"><span data-stu-id="4d732-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="4d732-104">La [méthode ExportType](exporttype-method.md) peut également exporter des types imbriqués, mais cette méthode est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="4d732-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d732-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d732-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4d732-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d732-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4d732-107">ID de l’assembly à partir duquel effectuer l’exportation.</span><span class="sxs-lookup"><span data-stu-id="4d732-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4d732-108">Jeton de fichier ou assembly de fichier qui définit le type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="4d732-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="4d732-109">Jeton de type de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="4d732-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="4d732-110">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="4d732-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="4d732-111">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="4d732-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4d732-112">`ComType`indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="4d732-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="4d732-113">Cette valeur peut être passée à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="4d732-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="4d732-114">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="4d732-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d732-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4d732-115">Return Value</span></span>  
 <span data-ttu-id="4d732-116">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="4d732-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d732-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4d732-117">Requirements</span></span>  
 <span data-ttu-id="4d732-118">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="4d732-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d732-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d732-119">See also</span></span>

- [<span data-ttu-id="4d732-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="4d732-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4d732-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="4d732-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4d732-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="4d732-122">ALink API</span></span>](index.md)
