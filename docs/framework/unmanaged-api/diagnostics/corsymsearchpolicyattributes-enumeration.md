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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7188c516d3d0a5192251697ec743e9d41f8d9072
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913736"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="bccf0-102">CorSymSearchPolicyAttributes, énumération</span><span class="sxs-lookup"><span data-stu-id="bccf0-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="bccf0-103">Spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="bccf0-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="bccf0-104">Ces constantes sont utilisées par les méthodes [ISymUnmanagedBinder2:: GetReaderForFile2,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) et [ISymUnmanagedBinder3:: GetReaderFromCallback,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bccf0-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bccf0-105">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="bccf0-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccf0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bccf0-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="bccf0-107">Membres</span><span class="sxs-lookup"><span data-stu-id="bccf0-107">Members</span></span>  
  
|<span data-ttu-id="bccf0-108">Membre</span><span class="sxs-lookup"><span data-stu-id="bccf0-108">Member</span></span>|<span data-ttu-id="bccf0-109">Description</span><span class="sxs-lookup"><span data-stu-id="bccf0-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="bccf0-110">Interroge le registre pour rechercher des chemins de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="bccf0-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="bccf0-111">Accède à un serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="bccf0-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="bccf0-112">Recherche le chemin d’accès spécifié dans le répertoire de débogage.</span><span class="sxs-lookup"><span data-stu-id="bccf0-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="bccf0-113">Recherche le fichier PDB à l’emplacement où se trouve le fichier. exe.</span><span class="sxs-lookup"><span data-stu-id="bccf0-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bccf0-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bccf0-114">Requirements</span></span>  
 <span data-ttu-id="bccf0-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bccf0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccf0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bccf0-116">See also</span></span>

- [<span data-ttu-id="bccf0-117">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="bccf0-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
