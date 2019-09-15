---
title: La référence d'assembly Friend <reference> n'est pas valide
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972394"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="2ed50-102">Le > de \<référence de l’assembly friend n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="2ed50-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="2ed50-103">Le > de \<référence d’assembly friend n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="2ed50-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="2ed50-104">Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="2ed50-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="2ed50-105">Le nom d’assembly passé <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> au constructeur d’attribut identifie un assembly avec nom fort, mais il n' `PublicKey` inclut pas d’attribut.</span><span class="sxs-lookup"><span data-stu-id="2ed50-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="2ed50-106">**ID d’erreur :** BC31535</span><span class="sxs-lookup"><span data-stu-id="2ed50-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ed50-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2ed50-107">To correct this error</span></span>  
  
1. <span data-ttu-id="2ed50-108">Déterminez la clé publique de l’assembly friend avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="2ed50-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="2ed50-109">Incluez la clé publique dans le nom de l’assembly passé <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> au constructeur d’attribut à `PublicKey` l’aide de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="2ed50-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed50-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ed50-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="2ed50-111">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="2ed50-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
