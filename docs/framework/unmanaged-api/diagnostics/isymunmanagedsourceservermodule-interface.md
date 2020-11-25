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
ms.openlocfilehash: 5e438c75a29984e9200dc240f389f079a4eecfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733952"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="edd03-102">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="edd03-102">ISymUnmanagedSourceServerModule Interface</span></span>

<span data-ttu-id="edd03-103">Fournit les données du serveur source pour un module.</span><span class="sxs-lookup"><span data-stu-id="edd03-103">Provides source server data for a module.</span></span> <span data-ttu-id="edd03-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="edd03-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="edd03-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="edd03-105">Methods</span></span>  
  
|<span data-ttu-id="edd03-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="edd03-106">Method</span></span>|<span data-ttu-id="edd03-107">Description</span><span class="sxs-lookup"><span data-stu-id="edd03-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="edd03-108">GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="edd03-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="edd03-109">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="edd03-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="edd03-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="edd03-110">Requirements</span></span>  

 <span data-ttu-id="edd03-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="edd03-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd03-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edd03-112">See also</span></span>

- [<span data-ttu-id="edd03-113">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="edd03-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
