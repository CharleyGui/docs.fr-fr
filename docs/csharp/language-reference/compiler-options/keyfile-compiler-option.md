---
description: -keyfile (Options du compilateur C#)
title: -keyfile (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: a97fc00201be1cf8043fc353b20ef447468a06bf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125486"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="176fa-103">-keyfile (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="176fa-103">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="176fa-104">Spécifie le nom du fichier contenant la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="176fa-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="176fa-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="176fa-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="176fa-106">Arguments</span></span>  
  
|<span data-ttu-id="176fa-107">Terme</span><span class="sxs-lookup"><span data-stu-id="176fa-107">Term</span></span>|<span data-ttu-id="176fa-108">Définition</span><span class="sxs-lookup"><span data-stu-id="176fa-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="176fa-109">Nom du fichier contenant la clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="176fa-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="176fa-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="176fa-110">Remarks</span></span>  
 <span data-ttu-id="176fa-111">Quand cette option est utilisée, le compilateur insère la clé publique du fichier spécifié dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="176fa-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="176fa-112">Pour générer un fichier de clé, tapez sn -k `file` sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="176fa-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="176fa-113">Si vous compilez avec **-target:module**, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="176fa-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="176fa-114">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="176fa-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="176fa-115">Utilisez [-delaysign](./delaysign-compiler-option.md) si vous voulez obtenir un assembly partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="176fa-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="176fa-116">Si -keyfile et -keycontainer sont spécifiés (par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur essaie d’abord d’utiliser le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="176fa-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="176fa-117">Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="176fa-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="176fa-118">Si le compilateur ne trouve pas le conteneur de clé, il essaie d’utiliser le fichier spécifié avec -keyfile.</span><span class="sxs-lookup"><span data-stu-id="176fa-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="176fa-119">En cas de réussite, l'assembly est signé avec les informations du fichier de clé et les informations sur la clé sont installées dans le conteneur de clé (semblable à sn -i) de sorte qu'à la compilation suivante, le conteneur de clé est valide.</span><span class="sxs-lookup"><span data-stu-id="176fa-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="176fa-120">Notez qu’un fichier de clé peut contenir uniquement la clé publique.</span><span class="sxs-lookup"><span data-stu-id="176fa-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="176fa-121">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) et [Différer la signature d’un assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="176fa-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="176fa-122">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="176fa-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="176fa-123">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="176fa-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="176fa-124">Cliquez sur la page de propriétés **Signature**.</span><span class="sxs-lookup"><span data-stu-id="176fa-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="176fa-125">Modifiez la propriété **Choisir un fichier de clé de nom fort**.</span><span class="sxs-lookup"><span data-stu-id="176fa-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="176fa-126">Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="176fa-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176fa-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="176fa-127">See also</span></span>

- [<span data-ttu-id="176fa-128">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="176fa-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="176fa-129">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="176fa-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
