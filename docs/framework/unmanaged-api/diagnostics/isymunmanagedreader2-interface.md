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
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709074"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="7daff-102">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="7daff-102">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="7daff-103">Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables d’un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="7daff-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="7daff-104">Cette interface étend l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7daff-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7daff-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7daff-105">Methods</span></span>  
  
|<span data-ttu-id="7daff-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="7daff-106">Method</span></span>|<span data-ttu-id="7daff-107">Description</span><span class="sxs-lookup"><span data-stu-id="7daff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7daff-108">GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="7daff-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="7daff-109">Obtenir une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="7daff-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="7daff-110">GetMethodsInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="7daff-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="7daff-111">Obtient toutes les méthodes qui ont des informations de ligne dans le document fourni.</span><span class="sxs-lookup"><span data-stu-id="7daff-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="7daff-112">GetSymAttributePreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="7daff-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="7daff-113">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="7daff-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7daff-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7daff-114">Requirements</span></span>  

 <span data-ttu-id="7daff-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7daff-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7daff-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7daff-116">See also</span></span>

- [<span data-ttu-id="7daff-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="7daff-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7daff-118">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="7daff-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
