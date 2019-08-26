---
title: Contenu d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1334f8c8e1b5898e93697461f609429d4aae764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921702"
---
# <a name="assembly-contents"></a><span data-ttu-id="12f5f-102">Contenu d'un assembly</span><span class="sxs-lookup"><span data-stu-id="12f5f-102">Assembly Contents</span></span>
<span data-ttu-id="12f5f-103">En général, un assembly statique peut comporter les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="12f5f-103">In general, a static assembly can consist of four elements:</span></span>  
  
- <span data-ttu-id="12f5f-104">Le [manifeste d’assembly](../../../docs/framework/app-domains/assembly-manifest.md), qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="12f5f-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
- <span data-ttu-id="12f5f-105">les métadonnées des types ;</span><span class="sxs-lookup"><span data-stu-id="12f5f-105">Type metadata.</span></span>  
  
- <span data-ttu-id="12f5f-106">le code MSIL (Microsoft Intermediate Language) qui implémente les types ;</span><span class="sxs-lookup"><span data-stu-id="12f5f-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
- <span data-ttu-id="12f5f-107">un ensemble de ressources.</span><span class="sxs-lookup"><span data-stu-id="12f5f-107">A set of resources.</span></span>  
  
 <span data-ttu-id="12f5f-108">Seul le manifeste d'assembly est requis, mais soit les types, soit les ressources sont nécessaires pour donner à l'assembly des fonctionnalités significatives.</span><span class="sxs-lookup"><span data-stu-id="12f5f-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="12f5f-109">Il existe plusieurs modes de regroupement de ces éléments dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="12f5f-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="12f5f-110">Vous pouvez regrouper tous les éléments dans un seul fichier physique, comme dans l'illustration ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="12f5f-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![Diagramme qui montre un assembly à fichier unique appelé MyAssembly.dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="12f5f-112">Les éléments d'un assembly peuvent également figurer dans plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="12f5f-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="12f5f-113">Ces fichiers peuvent être des modules de code compilé (.netmodule), des ressources (telles que des fichiers .bmp ou .jpg) ou d'autres fichiers requis par l'application.</span><span class="sxs-lookup"><span data-stu-id="12f5f-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="12f5f-114">Créez un assembly multifichier lorsque vous souhaitez associer des modules écrits dans différents langages et optimiser le téléchargement d'une application en mettant les types rarement utilisés dans un module qui n'est téléchargé qu'en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="12f5f-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="12f5f-115">Dans l'illustration ci-dessous, le développeur d'une application hypothétique a choisi de placer le code d'utilitaire dans un module distinct et de conserver un fichier de ressources volumineux (dans ce cas une image .bmp) dans son fichier d'origine.</span><span class="sxs-lookup"><span data-stu-id="12f5f-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="12f5f-116">Le .NET Framework ne télécharge un fichier que lorsqu'il est référencé ; le maintien du code peu référencé dans un fichier distinct de l'application optimise le téléchargement du code.</span><span class="sxs-lookup"><span data-stu-id="12f5f-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![Diagramme qui montre un assembly multifichier.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
> <span data-ttu-id="12f5f-118">Les fichiers qui composent un assembly multifichier ne sont pas physiquement reliés par le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="12f5f-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="12f5f-119">Ils sont à la place reliés par le manifeste d'assembly et le Common Language Runtime les manage en tant qu'unité.</span><span class="sxs-lookup"><span data-stu-id="12f5f-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="12f5f-120">Dans cette illustration, les trois fichiers appartiennent à un assembly, comme décrit dans le manifeste de l'assembly contenu dans MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="12f5f-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="12f5f-121">Pour le système de fichiers, il s'agit de trois fichiers distincts.</span><span class="sxs-lookup"><span data-stu-id="12f5f-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="12f5f-122">Notez que le fichier Util.netmodule a été compilé comme un module car il ne contient pas d'information sur l'assembly.</span><span class="sxs-lookup"><span data-stu-id="12f5f-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="12f5f-123">Lorsque l'assembly a été créé, le manifeste de l'assembly a été ajouté à MyAssembly.dll, en indiquant sa relation avec Util.netmodule et Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="12f5f-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="12f5f-124">Actuellement, à mesure que vous concevez votre code source, vous prenez des décisions explicites concernant le mode de partition des fonctionnalités de votre application dans un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="12f5f-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="12f5f-125">Lors du design de code .NET Framework, vous prendrez des décisions similaires sur le mode de partition des fonctionnalités dans un ou plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="12f5f-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f5f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12f5f-126">See also</span></span>

- [<span data-ttu-id="12f5f-127">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="12f5f-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="12f5f-128">Manifeste d’assembly</span><span class="sxs-lookup"><span data-stu-id="12f5f-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="12f5f-129">Aspects de la sécurité des assemblys</span><span class="sxs-lookup"><span data-stu-id="12f5f-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
