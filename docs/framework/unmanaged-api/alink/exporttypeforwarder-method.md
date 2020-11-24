---
title: ExportTypeForwarder, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 4e6ceabf37056bfc25247266be2c7801cb0e13e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684770"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="104e8-102">ExportTypeForwarder, méthode</span><span class="sxs-lookup"><span data-stu-id="104e8-102">ExportTypeForwarder Method</span></span>

<span data-ttu-id="104e8-103">Ajoute un redirecteur de type à la table de types de l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="104e8-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="104e8-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="104e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="104e8-105">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="104e8-106">Référence à l’assembly auquel le redirecteur de type fait référence.</span><span class="sxs-lookup"><span data-stu-id="104e8-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="104e8-107">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="104e8-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="104e8-108">`ComType` indicateurs tels que `tdPublic` ou `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="104e8-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="104e8-109">Cette valeur peut être passée à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="104e8-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="104e8-110">Reçoit le jeton du type exporté.</span><span class="sxs-lookup"><span data-stu-id="104e8-110">Receives the token of the exported type.</span></span> <span data-ttu-id="104e8-111">Cela est nécessaire uniquement pour l’émission de types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="104e8-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="104e8-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="104e8-112">Return Value</span></span>  

 <span data-ttu-id="104e8-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="104e8-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="104e8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="104e8-114">Requirements</span></span>  

 <span data-ttu-id="104e8-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="104e8-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104e8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="104e8-116">See also</span></span>

- [<span data-ttu-id="104e8-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="104e8-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="104e8-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="104e8-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="104e8-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="104e8-119">ALink API</span></span>](index.md)
