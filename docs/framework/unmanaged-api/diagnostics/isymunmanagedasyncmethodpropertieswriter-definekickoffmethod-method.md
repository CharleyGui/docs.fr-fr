---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 418a77855d1cb34a07f5957059b5a6f5a106c321
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707085"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="9d7ba-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="9d7ba-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="9d7ba-103">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9d7ba-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d7ba-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d7ba-105">Parameters</span></span>  
  
|<span data-ttu-id="9d7ba-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9d7ba-106">Parameter</span></span>|<span data-ttu-id="9d7ba-107">Description</span><span class="sxs-lookup"><span data-stu-id="9d7ba-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="9d7ba-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9d7ba-108">Return Value</span></span>  

 <span data-ttu-id="9d7ba-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9d7ba-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7ba-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d7ba-110">Requirements</span></span>  

 <span data-ttu-id="9d7ba-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9d7ba-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7ba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d7ba-112">See also</span></span>

- [<span data-ttu-id="9d7ba-113">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="9d7ba-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
