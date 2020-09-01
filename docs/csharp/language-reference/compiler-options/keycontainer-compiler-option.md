---
description: -keycontainer (Options du compilateur C#)
title: -keycontainer (Options du compilateur C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 8b11380683159b7792149558a5dd432707ba3818
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125499"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="3f963-103">-keycontainer (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3f963-103">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="3f963-104">Spécifie le nom du conteneur de la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="3f963-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f963-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f963-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f963-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="3f963-106">Arguments</span></span>  
 `string`  
 <span data-ttu-id="3f963-107">Nom du conteneur de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="3f963-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f963-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f963-108">Remarks</span></span>  
 <span data-ttu-id="3f963-109">Quand l’option **-keycontainer** est utilisée, le compilateur crée un composant pouvant être partagé.</span><span class="sxs-lookup"><span data-stu-id="3f963-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="3f963-110">Le compilateur insère une clé publique à partir du conteneur spécifié dans le manifeste d’assembly et signe l’assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="3f963-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="3f963-111">Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3f963-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="3f963-112">`sn -i` installe la paire de clés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f963-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="3f963-113">Cette option n’est pas prise en charge quand le compilateur s’exécute sur CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3f963-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="3f963-114">Pour signer un assembly en cas de génération sur CoreCLR, utilisez l’option [-keyfile](keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3f963-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="3f963-115">Si vous compilez avec [-target:module](./target-module-compiler-option.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly quand vous compilez ce module dans un assembly avec [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3f963-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3f963-116">Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) dans le code source de n'importe quel module MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3f963-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="3f963-117">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3f963-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="3f963-118">Utilisez [-delaysign](./delaysign-compiler-option.md) si vous voulez ajouter la clé publique au manifeste d’assembly, mais que vous voulez différer la signature de l’assembly tant qu’il n’a pas été testé.</span><span class="sxs-lookup"><span data-stu-id="3f963-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="3f963-119">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) et [Différer la signature d’un assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="3f963-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3f963-120">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f963-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3f963-121">Cette option de compilateur n’est pas disponible dans l'environnement de développement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f963-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="3f963-122">Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f963-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f963-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f963-123">See also</span></span>

- [<span data-ttu-id="3f963-124">Option -keyfile du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="3f963-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="3f963-125">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="3f963-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="3f963-126">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="3f963-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
