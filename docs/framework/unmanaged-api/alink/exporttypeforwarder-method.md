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
ms.openlocfilehash: 36c99477e9faead5e24799d5b0ae8901f1dd13c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448708"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="3c42e-102">ExportTypeForwarder, méthode</span><span class="sxs-lookup"><span data-stu-id="3c42e-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="3c42e-103">Ajoute un redirecteur de type à la table de types de l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="3c42e-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c42e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c42e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c42e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c42e-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="3c42e-106">Référence à l’assembly auquel le redirecteur de type fait référence.</span><span class="sxs-lookup"><span data-stu-id="3c42e-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="3c42e-107">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="3c42e-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3c42e-108">`ComType` indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="3c42e-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="3c42e-109">Cette valeur peut être passée à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c42e-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="3c42e-110">Reçoit le jeton du type exporté.</span><span class="sxs-lookup"><span data-stu-id="3c42e-110">Receives the token of the exported type.</span></span> <span data-ttu-id="3c42e-111">Cela est nécessaire uniquement pour l’émission de types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="3c42e-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c42e-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3c42e-112">Return Value</span></span>  
 <span data-ttu-id="3c42e-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="3c42e-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c42e-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c42e-114">Requirements</span></span>  
 <span data-ttu-id="3c42e-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="3c42e-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c42e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c42e-116">See also</span></span>

- [<span data-ttu-id="3c42e-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="3c42e-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3c42e-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="3c42e-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3c42e-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="3c42e-119">ALink API</span></span>](index.md)
