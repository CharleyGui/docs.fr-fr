---
title: ExportNestedTypeForwarder, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438410"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="d2fd7-102">ExportNestedTypeForwarder, méthode</span><span class="sxs-lookup"><span data-stu-id="d2fd7-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="d2fd7-103">Ajoute un redirecteur de type pour un type imbriqué à la table de types de l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2fd7-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2fd7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2fd7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d2fd7-106">ID de l’assembly à partir duquel effectuer l’exportation.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d2fd7-107">Jeton de fichier ou ID d’assembly du fichier qui définit le type.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="d2fd7-108">Jeton pour le type.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="d2fd7-109">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="d2fd7-110">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d2fd7-111">`ComType` indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="d2fd7-112">Reçoit le jeton de type d’exportation.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-112">Receives token of export type.</span></span> <span data-ttu-id="d2fd7-113">Cela est nécessaire uniquement pour l’émission de types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2fd7-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d2fd7-114">Return Value</span></span>  
 <span data-ttu-id="d2fd7-115">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="d2fd7-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2fd7-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2fd7-116">Requirements</span></span>  
 <span data-ttu-id="d2fd7-117">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="d2fd7-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fd7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2fd7-118">See also</span></span>

- [<span data-ttu-id="d2fd7-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d2fd7-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d2fd7-120">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d2fd7-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d2fd7-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="d2fd7-121">ALink API</span></span>](index.md)
