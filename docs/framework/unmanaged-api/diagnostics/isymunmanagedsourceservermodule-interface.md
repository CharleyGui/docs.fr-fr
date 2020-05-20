---
title: ISymUnmanagedSourceServerModule, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
ms.openlocfilehash: d90a55b53ba00540137e44fc190790c4710903e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610793"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="9c968-102">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="9c968-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="9c968-103">Fournit les données du serveur source pour un module.</span><span class="sxs-lookup"><span data-stu-id="9c968-103">Provides source server data for a module.</span></span> <span data-ttu-id="9c968-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9c968-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c968-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9c968-105">Methods</span></span>  
  
|<span data-ttu-id="9c968-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="9c968-106">Method</span></span>|<span data-ttu-id="9c968-107">Description</span><span class="sxs-lookup"><span data-stu-id="9c968-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c968-108">GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="9c968-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="9c968-109">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="9c968-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c968-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9c968-110">Requirements</span></span>  
 <span data-ttu-id="9c968-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9c968-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c968-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c968-112">See also</span></span>

- [<span data-ttu-id="9c968-113">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="9c968-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
