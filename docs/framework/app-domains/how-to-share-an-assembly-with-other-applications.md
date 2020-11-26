---
title: 'Procédure : Partager un assembly avec d’autres applications'
description: Découvrez comment partager un assembly avec d’autres applications dans .NET. Les assemblys peuvent être privés (valeur par défaut) ou partagés. Pour partager un assembly, placez-le dans le GAC.
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242537"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="c3a4e-105">Procédure : Partager un assembly avec d’autres applications</span><span class="sxs-lookup"><span data-stu-id="c3a4e-105">How to: Share an assembly with other applications</span></span>

<span data-ttu-id="c3a4e-106">Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="c3a4e-107">Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [global assembly cache (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="c3a4e-108">Pour partager un assembly :</span><span class="sxs-lookup"><span data-stu-id="c3a4e-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="c3a4e-109">Créez votre assembly.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-109">Create your assembly.</span></span> <span data-ttu-id="c3a4e-110">Pour plus d’informations, consultez [créer des assemblys](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="c3a4e-111">Attribuez un nom fort à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="c3a4e-112">Pour plus d’informations, consultez [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="c3a4e-113">Assignez des informations de version à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-113">Assign version information to your assembly.</span></span> <span data-ttu-id="c3a4e-114">Pour plus d’informations, consultez contrôle de [version des assemblys](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="c3a4e-115">Ajoutez votre assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="c3a4e-116">Pour plus d’informations, consultez [Comment : installer un assembly dans le global assembly cache](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="c3a4e-117">Accédez aux types contenus dans l’assembly à partir d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="c3a4e-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="c3a4e-118">Pour plus d’informations, consultez [Guide pratique pour référencer un assembly avec nom fort](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="c3a4e-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a4e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3a4e-119">See also</span></span>

- [<span data-ttu-id="c3a4e-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c3a4e-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="c3a4e-121">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3a4e-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="c3a4e-122">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="c3a4e-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
