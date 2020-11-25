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
ms.openlocfilehash: 5e3c2ecd1bdd5c1181223c7500eb7473e20fa5d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731343"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="0f0f5-102">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="0f0f5-102">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="0f0f5-103">Fournit des fonctions pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f0f5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0f0f5-104">Methods</span></span>  
  
|<span data-ttu-id="0f0f5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-105">Method</span></span>|<span data-ttu-id="0f0f5-106">Description</span><span class="sxs-lookup"><span data-stu-id="0f0f5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f0f5-107">GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="0f0f5-108">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="0f0f5-109">GetLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="0f0f5-110">Obtient les variables locales.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="0f0f5-111">InitializeForEnc, méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="0f0f5-112">Autorise le calcul des limites de méthode avant le premier appel à la méthode [ISymUnmanagedENCUpdate :: UpdateSymbolStore2,](isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f0f5-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="0f0f5-113">UpdateMethodLines, méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="0f0f5-114">Autorise la mise à jour des informations de ligne pour une méthode qui n’a pas été recompilée, mais dont les lignes ont été déplacées indépendamment.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="0f0f5-115">Un Delta est autorisé pour chaque instruction.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="0f0f5-116">UpdateSymbolStore2, méthode</span><span class="sxs-lookup"><span data-stu-id="0f0f5-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="0f0f5-117">Permet à un compilateur d’omettre les fonctions qui n’ont pas été modifiées à partir du flux de base de données du programme (PDB), à condition que les informations de ligne remplissent les conditions requises.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="0f0f5-118">Les informations de ligne correctes peuvent être déterminées par les anciennes informations de ligne PDB et un Delta pour toutes les lignes de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f0f5-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f0f5-119">Requirements</span></span>  

 <span data-ttu-id="0f0f5-120">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0f0f5-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0f5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f0f5-121">See also</span></span>

- [<span data-ttu-id="0f0f5-122">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0f0f5-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
