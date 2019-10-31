---
title: ISymUnmanagedWriter4, interface
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: a656777461c50b5a1593917278eb54abda982dc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134568"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="598c0-102">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="598c0-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="598c0-103">Interface Isymunmanagedwriter4,.</span><span class="sxs-lookup"><span data-stu-id="598c0-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="598c0-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="598c0-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="598c0-105">Methods</span></span>  
 <span data-ttu-id="598c0-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="598c0-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="598c0-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="598c0-107">Method</span></span>|<span data-ttu-id="598c0-108">Description</span><span class="sxs-lookup"><span data-stu-id="598c0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="598c0-109">GetDebugInfoWithPadding, méthode</span><span class="sxs-lookup"><span data-stu-id="598c0-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="598c0-110">Fonctionne de la même façon que la [méthode GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne de chemin d’accès est remplie de zéros après le caractère null de fin pour que les données de chaîne aient une taille fixe de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="598c0-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="598c0-111">Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="598c0-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="598c0-112">Cela facilite l’écriture d’outils qui différencient les fichiers PE.</span><span class="sxs-lookup"><span data-stu-id="598c0-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="598c0-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="598c0-113">Requirements</span></span>  
 <span data-ttu-id="598c0-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="598c0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598c0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="598c0-115">See also</span></span>

- [<span data-ttu-id="598c0-116">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="598c0-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="598c0-117">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="598c0-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
