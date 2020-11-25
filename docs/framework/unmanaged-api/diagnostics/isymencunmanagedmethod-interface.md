---
title: ISymENCUnmanagedMethod, interface
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707280"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="e0afd-102">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="e0afd-102">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="e0afd-103">Fournit des informations pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="e0afd-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0afd-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e0afd-104">Methods</span></span>  
  
|<span data-ttu-id="e0afd-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-105">Method</span></span>|<span data-ttu-id="e0afd-106">Description</span><span class="sxs-lookup"><span data-stu-id="e0afd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0afd-107">GetDocumentsForMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="e0afd-108">Obtient les documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="e0afd-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e0afd-109">GetDocumentsForMethodCount, méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="e0afd-110">Obtient le nombre de documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="e0afd-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e0afd-111">GetFileNameFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="e0afd-112">Obtient le nom de fichier pour la ligne associée à un offset.</span><span class="sxs-lookup"><span data-stu-id="e0afd-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="e0afd-113">GetLineFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="e0afd-114">Obtient les informations de ligne associées à un offset.</span><span class="sxs-lookup"><span data-stu-id="e0afd-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="e0afd-115">GetSourceExtentInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="e0afd-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="e0afd-116">Obtient la ligne de début la plus petite et la ligne de fin la plus grande pour la méthode dans un document spécifique.</span><span class="sxs-lookup"><span data-stu-id="e0afd-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0afd-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0afd-117">Requirements</span></span>  

 <span data-ttu-id="e0afd-118">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e0afd-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0afd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0afd-119">See also</span></span>

- [<span data-ttu-id="e0afd-120">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e0afd-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
