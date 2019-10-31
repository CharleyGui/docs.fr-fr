---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129170"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="423ab-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="423ab-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="423ab-103">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="423ab-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="423ab-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="423ab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="423ab-105">Parameters</span></span>  
  
|<span data-ttu-id="423ab-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="423ab-106">Parameter</span></span>|<span data-ttu-id="423ab-107">Description</span><span class="sxs-lookup"><span data-stu-id="423ab-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="423ab-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="423ab-108">Return Value</span></span>  
 <span data-ttu-id="423ab-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="423ab-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="423ab-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="423ab-110">Requirements</span></span>  
 <span data-ttu-id="423ab-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="423ab-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423ab-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="423ab-112">See also</span></span>

- [<span data-ttu-id="423ab-113">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="423ab-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
