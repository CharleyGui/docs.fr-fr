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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179414"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="980c0-102">ExportNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="980c0-102">ExportNestedType Method</span></span>
<span data-ttu-id="980c0-103">Spécifie les types imbriqués comme exportables.</span><span class="sxs-lookup"><span data-stu-id="980c0-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="980c0-104">La [méthode ExportType](exporttype-method.md) peut également exporter des types imbriqués, mais cette méthode est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="980c0-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="980c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="980c0-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="980c0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="980c0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="980c0-107">ID d’assemblage à l’exportation à partir de.</span><span class="sxs-lookup"><span data-stu-id="980c0-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="980c0-108">Jeton de fichier ou Assemblée de fichier qui définit le type à exporter.</span><span class="sxs-lookup"><span data-stu-id="980c0-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="980c0-109">Type de jeton de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="980c0-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="980c0-110">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="980c0-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="980c0-111">Nom de type entièrement qualifié à exporter.</span><span class="sxs-lookup"><span data-stu-id="980c0-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="980c0-112">`ComType`drapeaux tels `tdPublic` `tdNested`que ou .</span><span class="sxs-lookup"><span data-stu-id="980c0-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="980c0-113">Cette valeur peut être transmise à [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="980c0-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="980c0-114">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="980c0-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="980c0-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="980c0-115">Return Value</span></span>  
 <span data-ttu-id="980c0-116">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="980c0-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="980c0-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="980c0-117">Requirements</span></span>  
 <span data-ttu-id="980c0-118">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="980c0-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980c0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="980c0-119">See also</span></span>

- [<span data-ttu-id="980c0-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="980c0-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="980c0-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="980c0-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="980c0-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="980c0-122">ALink API</span></span>](index.md)
