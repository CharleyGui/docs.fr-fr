---
title: CorSymSearchPolicyAttributes, énumération
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178347"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="c5b79-102">CorSymSearchPolicyAttributes, énumération</span><span class="sxs-lookup"><span data-stu-id="c5b79-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="c5b79-103">Spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symbole.</span><span class="sxs-lookup"><span data-stu-id="c5b79-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="c5b79-104">Ces constantes sont utilisées par les méthodes [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) et [ISymUnmanmanagedBinder3:GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) méthodes.</span><span class="sxs-lookup"><span data-stu-id="c5b79-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5b79-105">C’est un risque pour la sécurité d’ouvrir un fichier de base de données de programme (PDB) à partir d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="c5b79-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b79-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5b79-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="c5b79-107">Membres</span><span class="sxs-lookup"><span data-stu-id="c5b79-107">Members</span></span>  
  
|<span data-ttu-id="c5b79-108">Membre</span><span class="sxs-lookup"><span data-stu-id="c5b79-108">Member</span></span>|<span data-ttu-id="c5b79-109">Description</span><span class="sxs-lookup"><span data-stu-id="c5b79-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="c5b79-110">Interroge le registre pour les chemins de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="c5b79-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="c5b79-111">Accéde à un serveur symbole.</span><span class="sxs-lookup"><span data-stu-id="c5b79-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="c5b79-112">Recherche le chemin spécifié dans l’annuaire Debug.</span><span class="sxs-lookup"><span data-stu-id="c5b79-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="c5b79-113">Recherche du PDB à l’endroit où se trouve le fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="c5b79-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5b79-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5b79-114">Requirements</span></span>  
 <span data-ttu-id="c5b79-115">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5b79-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b79-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5b79-116">See also</span></span>

- [<span data-ttu-id="c5b79-117">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="c5b79-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
