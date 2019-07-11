---
title: ExportType, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd1ec9caa70dd7016253ae4385b16dbfb982f956
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742022"
---
# <a name="exporttype-method"></a><span data-ttu-id="60551-102">ExportType, méthode</span><span class="sxs-lookup"><span data-stu-id="60551-102">ExportType Method</span></span>
<span data-ttu-id="60551-103">Spécifie qu’un type est exportable.</span><span class="sxs-lookup"><span data-stu-id="60551-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60551-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60551-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="60551-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60551-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="60551-106">ID de l’assembly à exporter à partir de.</span><span class="sxs-lookup"><span data-stu-id="60551-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="60551-107">Jeton ou l’assembly ID de fichier du fichier qui définit le type exportable.</span><span class="sxs-lookup"><span data-stu-id="60551-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="60551-108">Jeton de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="60551-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="60551-109">Nom de type qualifié complet à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="60551-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60551-110">`ComType` indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="60551-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="60551-111">Ce paramètre peut être passé à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="60551-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="60551-112">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="60551-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60551-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="60551-113">Return Value</span></span>  
 <span data-ttu-id="60551-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="60551-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60551-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="60551-115">Requirements</span></span>  
 <span data-ttu-id="60551-116">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="60551-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60551-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60551-117">See also</span></span>

- [<span data-ttu-id="60551-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="60551-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="60551-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="60551-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="60551-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="60551-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
