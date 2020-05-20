---
title: ISymUnmanagedWriter4, interface
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609467"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="ed4c8-102">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="ed4c8-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="ed4c8-103">Interface Isymunmanagedwriter4,.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed4c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed4c8-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="ed4c8-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ed4c8-105">Methods</span></span>  
 <span data-ttu-id="ed4c8-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed4c8-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ed4c8-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="ed4c8-107">Method</span></span>|<span data-ttu-id="ed4c8-108">Description</span><span class="sxs-lookup"><span data-stu-id="ed4c8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed4c8-109">GetDebugInfoWithPadding, méthode</span><span class="sxs-lookup"><span data-stu-id="ed4c8-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="ed4c8-110">Fonctionne de la même façon que la [méthode GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne du chemin d’accès est complétée par des zéros après le caractère null de fin pour que les données de la chaîne soient de taille fixe `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="ed4c8-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="ed4c8-111">Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="ed4c8-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="ed4c8-112">Cela facilite l’écriture d’outils qui différencient les fichiers PE.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed4c8-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ed4c8-113">Requirements</span></span>  
 <span data-ttu-id="ed4c8-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ed4c8-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4c8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed4c8-115">See also</span></span>

- [<span data-ttu-id="ed4c8-116">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="ed4c8-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ed4c8-117">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="ed4c8-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
