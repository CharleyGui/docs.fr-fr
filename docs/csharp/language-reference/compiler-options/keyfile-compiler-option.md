---
title: -keyfile (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970261"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="2f8c4-102">-keyfile (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="2f8c4-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="2f8c4-103">Spécifie le nom du fichier contenant la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8c4-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f8c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2f8c4-105">Arguments</span></span>  
  
|<span data-ttu-id="2f8c4-106">Terme</span><span class="sxs-lookup"><span data-stu-id="2f8c4-106">Term</span></span>|<span data-ttu-id="2f8c4-107">Définition</span><span class="sxs-lookup"><span data-stu-id="2f8c4-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="2f8c4-108">Nom du fichier contenant la clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f8c4-109">Notes </span><span class="sxs-lookup"><span data-stu-id="2f8c4-109">Remarks</span></span>  
 <span data-ttu-id="2f8c4-110">Quand cette option est utilisée, le compilateur insère la clé publique du fichier spécifié dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="2f8c4-111">Pour générer un fichier de clé, tapez sn -k `file` sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="2f8c4-112">Si vous compilez avec **-target:module**, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2f8c4-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="2f8c4-113">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2f8c4-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="2f8c4-114">Utilisez [-delaysign](./delaysign-compiler-option.md) si vous voulez obtenir un assembly partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="2f8c4-115">Si -keyfile et -keycontainer sont spécifiés (par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur essaie d’abord d’utiliser le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="2f8c4-116">Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="2f8c4-117">Si le compilateur ne trouve pas le conteneur de clé, il essaie d’utiliser le fichier spécifié avec -keyfile.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="2f8c4-118">En cas de réussite, l'assembly est signé avec les informations du fichier de clé et les informations sur la clé sont installées dans le conteneur de clé (semblable à sn -i) de sorte qu'à la compilation suivante, le conteneur de clé est valide.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="2f8c4-119">Notez qu’un fichier de clé peut contenir uniquement la clé publique.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="2f8c4-120">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) et [Différer la signature d’un assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="2f8c4-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2f8c4-121">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f8c4-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2f8c4-122">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="2f8c4-123">Cliquez sur la page de propriétés **Signature**.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="2f8c4-124">Modifiez la propriété **Choisir un fichier de clé de nom fort**.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="2f8c4-125">Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8c4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8c4-126">See also</span></span>

- [<span data-ttu-id="2f8c4-127">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="2f8c4-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2f8c4-128">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="2f8c4-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
