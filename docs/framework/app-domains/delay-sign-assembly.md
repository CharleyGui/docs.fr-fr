---
title: Temporisation de signature d'un assembly
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17034eb5dcb48ae43b8e0cd0bd0f49d0b0920a8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921609"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="59cc6-102">Temporisation de signature d'un assembly</span><span class="sxs-lookup"><span data-stu-id="59cc6-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="59cc6-103">Une entreprise peut avoir une paire de clés protégées auxquelles les développeurs n’ont pas accès tous les jours.</span><span class="sxs-lookup"><span data-stu-id="59cc6-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="59cc6-104">La clé publique est souvent disponible, mais l’accès à la clé privée est limité à quelques personnes.</span><span class="sxs-lookup"><span data-stu-id="59cc6-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="59cc6-105">Lors du développement d’assemblys avec des noms forts, chaque assembly qui référence l’assembly cible avec nom fort contient le jeton de la clé publique utilisée pour affecter un nom fort à l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="59cc6-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="59cc6-106">La clé publique doit donc être disponible pendant le processus de développement.</span><span class="sxs-lookup"><span data-stu-id="59cc6-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="59cc6-107">Vous pouvez utiliser la signature différée ou partielle au moment de la génération pour réserver de l’espace dans le fichier exécutable portable (PE) pour la signature de nom fort, mais différer la signature à une étape ultérieure (généralement juste avant de livrer l’assembly).</span><span class="sxs-lookup"><span data-stu-id="59cc6-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="59cc6-108">Les étapes suivantes décrivent le processus permettant de différer la signature d’un assembly :</span><span class="sxs-lookup"><span data-stu-id="59cc6-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1. <span data-ttu-id="59cc6-109">Obtenez la partie clé publique de la paire de clés auprès de la société qui effectuera la signature.</span><span class="sxs-lookup"><span data-stu-id="59cc6-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="59cc6-110">En règle générale, cette clé se présente sous la forme d’un fichier .snk, qui peut être créé avec l’[outil Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) fourni par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="59cc6-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>  
  
2. <span data-ttu-id="59cc6-111">Annotez le code source de l’assembly avec deux attributs personnalisés de <xref:System.Reflection> :</span><span class="sxs-lookup"><span data-stu-id="59cc6-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    - <span data-ttu-id="59cc6-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="59cc6-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    - <span data-ttu-id="59cc6-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, qui indique l’utilisation de la temporisation de signature en passant **true** comme paramètre à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="59cc6-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="59cc6-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="59cc6-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. <span data-ttu-id="59cc6-115">Le compilateur insère la clé publique dans le manifeste d’assembly et réserve de l’espace dans le fichier PE pour la signature de nom fort complète.</span><span class="sxs-lookup"><span data-stu-id="59cc6-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="59cc6-116">La clé publique réelle doit être stockée lors de la génération de l’assembly, de sorte que d’autres assemblys référençant cet assembly puissent obtenir la clé à stocker dans leur propre référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="59cc6-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4. <span data-ttu-id="59cc6-117">Étant donné que l’assembly n’a pas de signature de nom fort valide, la vérification de cette signature doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="59cc6-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="59cc6-118">Vous pouvez pour cela utiliser l’option **–Vr** avec l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="59cc6-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="59cc6-119">L’exemple suivant désactive la vérification pour un assembly nommé `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="59cc6-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="59cc6-120">Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l’outil Strong Name, telles que les microprocesseurs ARM (Advanced RISC Machine), utilisez l’option **–Vk** pour créer un fichier de Registre.</span><span class="sxs-lookup"><span data-stu-id="59cc6-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="59cc6-121">Importez le fichier de Registre dans le Registre sur l’ordinateur sur lequel vous souhaitez désactiver la vérification.</span><span class="sxs-lookup"><span data-stu-id="59cc6-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="59cc6-122">L’exemple suivant crée un fichier de Registre pour `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="59cc6-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="59cc6-123">Avec l’option **–Vr** ou **–Vk**, vous pouvez éventuellement inclure un fichier .snk pour la signature de clé test.</span><span class="sxs-lookup"><span data-stu-id="59cc6-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="59cc6-124">Ne comptez pas sur les noms forts pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="59cc6-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="59cc6-125">Ils fournissent seulement une identité unique.</span><span class="sxs-lookup"><span data-stu-id="59cc6-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="59cc6-126">Si vous utilisez la temporisation de signature lors du développement avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour **Any CPU**, vous devrez peut-être appliquer deux fois l’option **-Vr**.</span><span class="sxs-lookup"><span data-stu-id="59cc6-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="59cc6-127">(Dans Visual Studio, **Any CPU** est une valeur de la propriété de build **Plateforme cible** ; quand vous compilez à partir de la ligne de commande, il s’agit de la valeur par défaut.) Pour exécuter votre application à partir de la ligne de commande ou de l’Explorateur de fichiers, utilisez la version 64 bits de [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pour appliquer l’option **-Vr** à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="59cc6-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="59cc6-128">Pour charger l’assembly dans Visual Studio au moment du design (par exemple, si l’assembly contient des composants utilisés par d’autres assemblys dans votre application), utilisez la version 32 bits de l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="59cc6-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="59cc6-129">Ceci s’explique par le fait que le compilateur juste-à-temps (JIT) compile l’assembly en code natif 64 bits quand l’assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits quand l’assembly est chargé dans l’environnement au moment du design.</span><span class="sxs-lookup"><span data-stu-id="59cc6-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5. <span data-ttu-id="59cc6-130">Vous soumettez l’assembly ultérieurement, généralement juste avant sa livraison, à l’Autorité de signature de votre organisation pour la signature réelle de nom fort en utilisant l’option **–R** avec l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="59cc6-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="59cc6-131">L’exemple suivant signe un assembly nommé `myAssembly.dll` avec un nom fort à l’aide de la paire de clés `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="59cc6-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59cc6-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59cc6-132">See also</span></span>

- [<span data-ttu-id="59cc6-133">Création d’assemblys</span><span class="sxs-lookup"><span data-stu-id="59cc6-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="59cc6-134">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="59cc6-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="59cc6-135">Sn.exe (outil Strong Name)</span><span class="sxs-lookup"><span data-stu-id="59cc6-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="59cc6-136">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="59cc6-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
