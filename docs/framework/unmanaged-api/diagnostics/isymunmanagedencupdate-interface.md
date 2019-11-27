---
title: ISymUnmanagedENCUpdate, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449004"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="37491-102">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="37491-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="37491-103">Fournit des fonctions pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="37491-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37491-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="37491-104">Methods</span></span>  
  
|<span data-ttu-id="37491-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="37491-105">Method</span></span>|<span data-ttu-id="37491-106">Description</span><span class="sxs-lookup"><span data-stu-id="37491-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37491-107">GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="37491-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="37491-108">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="37491-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="37491-109">GetLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="37491-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="37491-110">Obtient les variables locales.</span><span class="sxs-lookup"><span data-stu-id="37491-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="37491-111">InitializeForEnc, méthode</span><span class="sxs-lookup"><span data-stu-id="37491-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="37491-112">Autorise le calcul des limites de méthode avant le premier appel à la méthode [ISymUnmanagedENCUpdate :: UpdateSymbolStore2,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37491-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="37491-113">UpdateMethodLines, méthode</span><span class="sxs-lookup"><span data-stu-id="37491-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="37491-114">Autorise la mise à jour des informations de ligne pour une méthode qui n’a pas été recompilée, mais dont les lignes ont été déplacées indépendamment.</span><span class="sxs-lookup"><span data-stu-id="37491-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="37491-115">Un Delta est autorisé pour chaque instruction.</span><span class="sxs-lookup"><span data-stu-id="37491-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="37491-116">UpdateSymbolStore2, méthode</span><span class="sxs-lookup"><span data-stu-id="37491-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="37491-117">Permet à un compilateur d’omettre les fonctions qui n’ont pas été modifiées à partir du flux de base de données du programme (PDB), à condition que les informations de ligne remplissent les conditions requises.</span><span class="sxs-lookup"><span data-stu-id="37491-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="37491-118">Les informations de ligne correctes peuvent être déterminées par les anciennes informations de ligne PDB et un Delta pour toutes les lignes de la fonction.</span><span class="sxs-lookup"><span data-stu-id="37491-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37491-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="37491-119">Requirements</span></span>  
 <span data-ttu-id="37491-120">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="37491-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37491-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37491-121">See also</span></span>

- [<span data-ttu-id="37491-122">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="37491-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
