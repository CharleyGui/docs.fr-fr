---
title: La référence d'assembly Friend <reference> n'est pas valide
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 72c030d18d5339908c5088e104f6a8ad3e76943b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874096"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="d3b6a-102">La référence d'assembly Friend \<reference> n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="d3b6a-102">Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="d3b6a-103">La référence d’assembly friend \<reference> n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="d3b6a-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="d3b6a-104">Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="d3b6a-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="d3b6a-105">Le nom d’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas d' `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="d3b6a-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="d3b6a-106">**ID d’erreur :** BC31535</span><span class="sxs-lookup"><span data-stu-id="d3b6a-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3b6a-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d3b6a-107">To correct this error</span></span>  
  
1. <span data-ttu-id="d3b6a-108">Déterminez la clé publique de l’assembly friend avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="d3b6a-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="d3b6a-109">Incluez la clé publique dans le nom de l’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de l' `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="d3b6a-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b6a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3b6a-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="d3b6a-111">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="d3b6a-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
