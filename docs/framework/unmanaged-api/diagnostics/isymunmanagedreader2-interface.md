---
title: ISymUnmanagedReader2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: a07c75e14244fb5bdf72ff2b0d344ae27672ef89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448267"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="4263c-102">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="4263c-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="4263c-103">Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="4263c-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="4263c-104">Cette interface étend l’interface [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4263c-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4263c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4263c-105">Methods</span></span>  
  
|<span data-ttu-id="4263c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4263c-106">Method</span></span>|<span data-ttu-id="4263c-107">Description</span><span class="sxs-lookup"><span data-stu-id="4263c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4263c-108">GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="4263c-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="4263c-109">Obtenir une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="4263c-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="4263c-110">GetMethodsInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="4263c-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="4263c-111">Obtient toutes les méthodes qui ont des informations de ligne dans le document fourni.</span><span class="sxs-lookup"><span data-stu-id="4263c-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="4263c-112">GetSymAttributePreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="4263c-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="4263c-113">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="4263c-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4263c-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4263c-114">Requirements</span></span>  
 <span data-ttu-id="4263c-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4263c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4263c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4263c-116">See also</span></span>

- [<span data-ttu-id="4263c-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="4263c-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="4263c-118">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="4263c-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
