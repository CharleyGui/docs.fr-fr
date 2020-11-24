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
ms.openlocfilehash: 69c99e2facfcb9077c3fc4131186ba3882c7cef6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684835"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="1da05-102">ExportNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="1da05-102">ExportNestedType Method</span></span>

<span data-ttu-id="1da05-103">Spécifie que les types imbriqués sont exportables.</span><span class="sxs-lookup"><span data-stu-id="1da05-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="1da05-104">La [méthode ExportType](exporttype-method.md) peut également exporter des types imbriqués, mais cette méthode est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="1da05-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da05-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da05-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1da05-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1da05-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="1da05-107">ID de l’assembly à partir duquel effectuer l’exportation.</span><span class="sxs-lookup"><span data-stu-id="1da05-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1da05-108">Jeton de fichier ou assembly de fichier qui définit le type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="1da05-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="1da05-109">Jeton de type de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="1da05-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="1da05-110">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="1da05-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1da05-111">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="1da05-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1da05-112">`ComType` indicateurs tels que `tdPublic` ou `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="1da05-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="1da05-113">Cette valeur peut être passée à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="1da05-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="1da05-114">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="1da05-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1da05-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1da05-115">Return Value</span></span>  

 <span data-ttu-id="1da05-116">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="1da05-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da05-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1da05-117">Requirements</span></span>  

 <span data-ttu-id="1da05-118">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="1da05-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da05-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1da05-119">See also</span></span>

- [<span data-ttu-id="1da05-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="1da05-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1da05-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="1da05-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1da05-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="1da05-122">ALink API</span></span>](index.md)
