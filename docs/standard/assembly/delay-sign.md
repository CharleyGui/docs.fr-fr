---
title: Temporiser la signature d’un assembly
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733162"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="e56bf-102">Temporiser la signature d’un assembly</span><span class="sxs-lookup"><span data-stu-id="e56bf-102">Delay-sign an assembly</span></span>

<span data-ttu-id="e56bf-103">Une organisation peut avoir une paire de clés étroitement protégée que les développeurs ne peuvent pas accéder quotidiennement.</span><span class="sxs-lookup"><span data-stu-id="e56bf-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="e56bf-104">La clé publique est souvent disponible, mais l’accès à la clé privée est limité à quelques personnes.</span><span class="sxs-lookup"><span data-stu-id="e56bf-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="e56bf-105">Lors du développement d’assemblys avec des noms forts, chaque assembly qui référence l’assembly cible avec nom fort contient le jeton de la clé publique utilisée pour affecter un nom fort à l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="e56bf-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="e56bf-106">La clé publique doit donc être disponible pendant le processus de développement.</span><span class="sxs-lookup"><span data-stu-id="e56bf-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="e56bf-107">Vous pouvez utiliser la signature différée ou partielle au moment de la génération pour réserver de l’espace dans le fichier exécutable portable (PE) pour la signature de nom fort, mais différer la signature réelle jusqu’à une étape ultérieure, généralement juste avant la livraison de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e56bf-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="e56bf-108">Pour différer la signature d’un assembly :</span><span class="sxs-lookup"><span data-stu-id="e56bf-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="e56bf-109">Récupérez la partie clé publique de la paire de clés de l’organisation qui effectuera la signature finale.</span><span class="sxs-lookup"><span data-stu-id="e56bf-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="e56bf-110">En général, cette clé se présente sous la forme d’un fichier *. snk* , qui peut être créé à l’aide de l' [outil Strong Name Tool (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) fourni par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="e56bf-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="e56bf-111">Annotez le code source de l’assembly avec deux attributs personnalisés de <xref:System.Reflection> :</span><span class="sxs-lookup"><span data-stu-id="e56bf-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="e56bf-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="e56bf-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="e56bf-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, qui indique l’utilisation de la temporisation de signature en passant **true** comme paramètre à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="e56bf-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="e56bf-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e56bf-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="e56bf-115">Le compilateur insère la clé publique dans le manifeste d’assembly et réserve de l’espace dans le fichier PE pour la signature de nom fort complète.</span><span class="sxs-lookup"><span data-stu-id="e56bf-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="e56bf-116">La clé publique réelle doit être stockée lors de la génération de l’assembly, de sorte que d’autres assemblys référençant cet assembly puissent obtenir la clé à stocker dans leur propre référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e56bf-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="e56bf-117">Étant donné que l’assembly n’a pas de signature de nom fort valide, la vérification de cette signature doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="e56bf-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="e56bf-118">Vous pouvez pour cela utiliser l’option **–Vr** avec l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="e56bf-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="e56bf-119">L’exemple suivant désactive la vérification d’un assembly appelé *myAssembly. dll*.</span><span class="sxs-lookup"><span data-stu-id="e56bf-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="e56bf-120">Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l’outil Strong Name, telles que les microprocesseurs ARM (Advanced RISC Machine), utilisez l’option **–Vk** pour créer un fichier de Registre.</span><span class="sxs-lookup"><span data-stu-id="e56bf-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="e56bf-121">Importez le fichier de Registre dans le Registre sur l’ordinateur sur lequel vous souhaitez désactiver la vérification.</span><span class="sxs-lookup"><span data-stu-id="e56bf-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="e56bf-122">L’exemple suivant crée un fichier de Registre pour `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e56bf-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="e56bf-123">Avec l’option **– VR** ou **– VK** , vous pouvez éventuellement inclure un fichier *. snk* pour la signature de la clé de test.</span><span class="sxs-lookup"><span data-stu-id="e56bf-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="e56bf-124">Ne comptez pas sur les noms forts pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e56bf-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="e56bf-125">Ils fournissent seulement une identité unique.</span><span class="sxs-lookup"><span data-stu-id="e56bf-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e56bf-126">Si vous utilisez la temporisation de signature lors du développement avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour **Any CPU**, vous devrez peut-être appliquer deux fois l’option **-Vr**.</span><span class="sxs-lookup"><span data-stu-id="e56bf-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="e56bf-127">(Dans Visual Studio, **toute UC** est une valeur de la propriété de build cible de la **plateforme** ; quand vous compilez à partir de la ligne de commande, il s’agit de la valeur par défaut.) Pour exécuter votre application à partir de la ligne de commande ou de l’Explorateur de fichiers, utilisez la version 64 bits de [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md) pour appliquer l’option **-VR** à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e56bf-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="e56bf-128">Pour charger l’assembly dans Visual Studio au moment du design (par exemple, si l’assembly contient des composants utilisés par d’autres assemblys dans votre application), utilisez la version 32 bits de l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="e56bf-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="e56bf-129">Ceci s’explique par le fait que le compilateur juste-à-temps (JIT) compile l’assembly en code natif 64 bits quand l’assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits quand l’assembly est chargé dans l’environnement au moment du design.</span><span class="sxs-lookup"><span data-stu-id="e56bf-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="e56bf-130">Vous soumettez l’assembly ultérieurement, généralement juste avant sa livraison, à l’Autorité de signature de votre organisation pour la signature réelle de nom fort en utilisant l’option **–R** avec l’outil Strong Name.</span><span class="sxs-lookup"><span data-stu-id="e56bf-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="e56bf-131">L’exemple suivant signe un assembly appelé *myAssembly. dll* avec un nom fort à l’aide de la paire de clés *sgKey. snk* .</span><span class="sxs-lookup"><span data-stu-id="e56bf-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="e56bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e56bf-132">See also</span></span>

- [<span data-ttu-id="e56bf-133">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="e56bf-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="e56bf-134">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="e56bf-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="e56bf-135">SN. exe (outil Strong Name Tool)</span><span class="sxs-lookup"><span data-stu-id="e56bf-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
