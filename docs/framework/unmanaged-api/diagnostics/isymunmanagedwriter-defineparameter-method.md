---
title: ISymUnmanagedWriter::DefineParameter, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: c695aa80ea3bf90a29ce7c5d11eda7fae5fe7b2d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614810"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="efe8d-102">ISymUnmanagedWriter::DefineParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="efe8d-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="efe8d-103">Définit un paramètre unique dans la méthode en cours.</span><span class="sxs-lookup"><span data-stu-id="efe8d-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="efe8d-104">Le type de paramètre est extrait de la position (séquence) du paramètre dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="efe8d-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="efe8d-105">Si des paramètres sont définis dans les métadonnées d’une méthode donnée, vous n’avez pas à les redéfinir à l’aide de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="efe8d-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="efe8d-106">Les lecteurs de symboles doivent vérifier les métadonnées normales des paramètres avant de vérifier le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="efe8d-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe8d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efe8d-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efe8d-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efe8d-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="efe8d-109">dans Nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="efe8d-110">dans Attributs du paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="efe8d-111">dans Signature du paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="efe8d-112">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="efe8d-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="efe8d-113">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="efe8d-114">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="efe8d-115">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="efe8d-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efe8d-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="efe8d-116">Return Value</span></span>  
 <span data-ttu-id="efe8d-117">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="efe8d-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe8d-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="efe8d-118">Requirements</span></span>  
 <span data-ttu-id="efe8d-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="efe8d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe8d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efe8d-120">See also</span></span>

- [<span data-ttu-id="efe8d-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="efe8d-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
