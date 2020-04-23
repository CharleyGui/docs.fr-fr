---
title: 'Comment : partager un assembly avec d’autres applications'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644288"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="d5026-102">Comment : partager un assembly avec d’autres applications</span><span class="sxs-lookup"><span data-stu-id="d5026-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="d5026-103">Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="d5026-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="d5026-104">Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [global assembly cache (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="d5026-105">Pour partager un assembly :</span><span class="sxs-lookup"><span data-stu-id="d5026-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="d5026-106">Créez votre assembly.</span><span class="sxs-lookup"><span data-stu-id="d5026-106">Create your assembly.</span></span> <span data-ttu-id="d5026-107">Pour plus d’informations, consultez [créer des assemblys](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="d5026-108">Attribuez un nom fort à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="d5026-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="d5026-109">Pour plus d’informations, consultez [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="d5026-110">Assignez des informations de version à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="d5026-110">Assign version information to your assembly.</span></span> <span data-ttu-id="d5026-111">Pour plus d’informations, consultez contrôle de [version des assemblys](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="d5026-112">Ajoutez votre assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="d5026-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="d5026-113">Pour plus d’informations, consultez [Comment : installer un assembly dans le global assembly cache](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="d5026-114">Accédez aux types contenus dans l’assembly à partir d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="d5026-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="d5026-115">Pour plus d’informations, consultez [Guide pratique pour référencer un assembly avec nom fort](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="d5026-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5026-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5026-116">See also</span></span>

- [<span data-ttu-id="d5026-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d5026-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="d5026-118">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5026-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="d5026-119">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="d5026-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
