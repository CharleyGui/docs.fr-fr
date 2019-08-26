---
title: 'Procédure : Partager un assembly avec d’autres applications (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595734"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="5c517-102">Procédure : Partager un assembly avec d’autres applications (C#)</span><span class="sxs-lookup"><span data-stu-id="5c517-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="5c517-103">Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="5c517-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="5c517-104">Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="5c517-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="5c517-105">Partage d’un assembly</span><span class="sxs-lookup"><span data-stu-id="5c517-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="5c517-106">Créez votre assembly.</span><span class="sxs-lookup"><span data-stu-id="5c517-106">Create your assembly.</span></span> <span data-ttu-id="5c517-107">Pour plus d’informations, consultez [Création d’assemblys](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5c517-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="5c517-108">Attribuez un nom fort à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="5c517-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="5c517-109">Pour plus d'informations, voir [Procédure : signer un assembly avec un nom fort](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="5c517-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="5c517-110">Assignez des informations de version à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="5c517-110">Assign version information to your assembly.</span></span> <span data-ttu-id="5c517-111">Pour plus d’informations, consultez [Versioning des assemblys](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="5c517-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="5c517-112">Ajoutez votre assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="5c517-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="5c517-113">Pour plus d'informations, voir [Procédure : Installer un assembly dans le Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="5c517-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="5c517-114">Accédez aux types contenus dans l’assembly à partir d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="5c517-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="5c517-115">Pour plus d'informations, voir [Procédure : Référencer un assembly avec un nom fort](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5c517-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c517-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c517-116">See also</span></span>

- [<span data-ttu-id="5c517-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5c517-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="5c517-118">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="5c517-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
