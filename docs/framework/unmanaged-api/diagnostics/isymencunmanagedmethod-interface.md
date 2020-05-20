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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441875"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="73275-102">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="73275-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="73275-103">Fournit des informations pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="73275-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73275-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="73275-104">Methods</span></span>  
  
|<span data-ttu-id="73275-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="73275-105">Method</span></span>|<span data-ttu-id="73275-106">Description</span><span class="sxs-lookup"><span data-stu-id="73275-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73275-107">GetDocumentsForMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="73275-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="73275-108">Obtient les documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="73275-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="73275-109">GetDocumentsForMethodCount, méthode</span><span class="sxs-lookup"><span data-stu-id="73275-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="73275-110">Obtient le nombre de documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="73275-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="73275-111">GetFileNameFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="73275-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="73275-112">Obtient le nom de fichier pour la ligne associée à un offset.</span><span class="sxs-lookup"><span data-stu-id="73275-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="73275-113">GetLineFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="73275-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="73275-114">Obtient les informations de ligne associées à un offset.</span><span class="sxs-lookup"><span data-stu-id="73275-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="73275-115">GetSourceExtentInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="73275-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="73275-116">Obtient la ligne de début la plus petite et la ligne de fin la plus grande pour la méthode dans un document spécifique.</span><span class="sxs-lookup"><span data-stu-id="73275-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73275-117">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="73275-117">Requirements</span></span>  
 <span data-ttu-id="73275-118">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="73275-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73275-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73275-119">See also</span></span>

- [<span data-ttu-id="73275-120">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="73275-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
