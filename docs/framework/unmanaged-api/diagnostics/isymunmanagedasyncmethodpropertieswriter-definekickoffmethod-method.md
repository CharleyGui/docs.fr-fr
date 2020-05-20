---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: c35455fc679d79d56814a9c2f026ec395e944f24
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441719"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="fe216-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="fe216-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="fe216-103">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="fe216-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe216-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe216-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe216-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe216-105">Parameters</span></span>  
  
|<span data-ttu-id="fe216-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fe216-106">Parameter</span></span>|<span data-ttu-id="fe216-107">Description</span><span class="sxs-lookup"><span data-stu-id="fe216-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="fe216-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fe216-108">Return Value</span></span>  
 <span data-ttu-id="fe216-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fe216-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe216-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="fe216-110">Requirements</span></span>  
 <span data-ttu-id="fe216-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe216-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe216-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe216-112">See also</span></span>

- [<span data-ttu-id="fe216-113">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="fe216-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
