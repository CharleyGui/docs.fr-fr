---
title: ISymUnmanagedVariable, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 93e1f8eb17f06e42ddb243f88c593979fcb28030
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733280"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="63b47-102">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="63b47-102">ISymUnmanagedVariable Interface</span></span>

<span data-ttu-id="63b47-103">Représente une variable, comme un paramètre, une variable locale ou un champ.</span><span class="sxs-lookup"><span data-stu-id="63b47-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63b47-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="63b47-104">Methods</span></span>  
  
|<span data-ttu-id="63b47-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-105">Method</span></span>|<span data-ttu-id="63b47-106">Description</span><span class="sxs-lookup"><span data-stu-id="63b47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63b47-107">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="63b47-108">Obtient le premier champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="63b47-109">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="63b47-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="63b47-110">GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="63b47-111">Obtient le deuxième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="63b47-112">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="63b47-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="63b47-113">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="63b47-114">Obtient le troisième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="63b47-115">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="63b47-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="63b47-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="63b47-117">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="63b47-118">GetAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="63b47-119">Obtient les indicateurs d’attribut pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="63b47-120">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="63b47-121">Obtient le décalage de fin de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="63b47-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="63b47-122">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="63b47-123">Obtient le nom de cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="63b47-124">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="63b47-125">Obtient la signature de cette variable.</span><span class="sxs-lookup"><span data-stu-id="63b47-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="63b47-126">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="63b47-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="63b47-127">Obtient le décalage de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="63b47-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63b47-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="63b47-128">Requirements</span></span>  

 <span data-ttu-id="63b47-129">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="63b47-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b47-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63b47-130">See also</span></span>

- [<span data-ttu-id="63b47-131">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="63b47-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
