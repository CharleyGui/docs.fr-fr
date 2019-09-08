---
title: GetScope, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a0e42e9ffb99896bdd09dbbab65eafb40cafff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777208"
---
# <a name="getscope-method"></a><span data-ttu-id="860c1-102">GetScope, méthode</span><span class="sxs-lookup"><span data-stu-id="860c1-102">GetScope Method</span></span>
<span data-ttu-id="860c1-103">Obtient une étendue d’importation.</span><span class="sxs-lookup"><span data-stu-id="860c1-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="860c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="860c1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="860c1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="860c1-106">ID unique de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="860c1-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="860c1-107">ID unique du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="860c1-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="860c1-108">Étendue de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="860c1-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="860c1-109">Reçoit l’interface d' [interface IMetaDataImport](../metadata/imetadataimport-interface.md) pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="860c1-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="860c1-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="860c1-110">Return Value</span></span>  
 <span data-ttu-id="860c1-111">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="860c1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860c1-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="860c1-112">Requirements</span></span>  
 <span data-ttu-id="860c1-113">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="860c1-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860c1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="860c1-114">See also</span></span>

- [<span data-ttu-id="860c1-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="860c1-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="860c1-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="860c1-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="860c1-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="860c1-117">ALink API</span></span>](index.md)
