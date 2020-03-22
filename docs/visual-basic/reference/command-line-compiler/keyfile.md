---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266740"
---
# <a name="-keyfile"></a><span data-ttu-id="996bf-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="996bf-102">-keyfile</span></span>
<span data-ttu-id="996bf-103">Spécifie un fichier contenant une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.</span><span class="sxs-lookup"><span data-stu-id="996bf-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="996bf-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="996bf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="996bf-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="996bf-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="996bf-106">Required.</span></span> <span data-ttu-id="996bf-107">Fichier qui contient la clé.</span><span class="sxs-lookup"><span data-stu-id="996bf-107">File that contains the key.</span></span> <span data-ttu-id="996bf-108">Si le nom du fichier contient un espace, insécrez le nom dans des guillemets (" ").</span><span class="sxs-lookup"><span data-stu-id="996bf-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996bf-109">Notes </span><span class="sxs-lookup"><span data-stu-id="996bf-109">Remarks</span></span>  
 <span data-ttu-id="996bf-110">Le compilateur insère la clé publique dans le manifeste de l’assemblage, puis signe l’assemblage final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="996bf-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="996bf-111">Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="996bf-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="996bf-112">Pour plus d’informations, voir [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="996bf-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="996bf-113">Si vous compilez avec `-target:module`, le nom du fichier clé est conservé dans le module et incorporé dans l’assemblage qui est créé lorsque vous compilez un assemblage avec [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="996bf-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="996bf-114">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="996bf-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="996bf-115">Utilisez [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous voulez obtenir un assembly partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="996bf-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="996bf-116">Vous pouvez également spécifier<xref:System.Reflection.AssemblyKeyFileAttribute>cette option comme un attribut personnalisé ( ) dans le code source pour n’importe quel module de langue intermédiaire Microsoft.</span><span class="sxs-lookup"><span data-stu-id="996bf-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="996bf-117">Dans le `-keyfile` cas où les deux et [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sont spécifiés (soit par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur tente d’abord le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="996bf-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="996bf-118">Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="996bf-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="996bf-119">Si le compilateur ne trouve pas le conteneur `-keyfile`clé, il essaie le fichier spécifié avec .</span><span class="sxs-lookup"><span data-stu-id="996bf-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="996bf-120">Si cela réussit, l’assemblage est signé avec les informations contenues dans le fichier `sn -i`clé, et les informations clés sont installées dans le conteneur clé (similaire à ) de sorte que sur la prochaine compilation, le conteneur clé sera valide.</span><span class="sxs-lookup"><span data-stu-id="996bf-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="996bf-121">Notez qu’un fichier de clé peut contenir uniquement la clé publique.</span><span class="sxs-lookup"><span data-stu-id="996bf-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="996bf-122">Voir [Créer et utiliser des assemblées nommées pour](../../../standard/assembly/create-use-strong-named.md) plus d’informations sur la signature d’une assemblée.</span><span class="sxs-lookup"><span data-stu-id="996bf-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="996bf-123">L’option `-keyfile` n’est pas disponible dans l’environnement de développement Visual Studio; il n’est disponible que lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="996bf-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="996bf-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="996bf-124">Example</span></span>

<span data-ttu-id="996bf-125">Le code suivant compile le fichier `Input.vb` source et spécifie un fichier clé.</span><span class="sxs-lookup"><span data-stu-id="996bf-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="996bf-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="996bf-126">See also</span></span>

- [<span data-ttu-id="996bf-127">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="996bf-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="996bf-128">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="996bf-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="996bf-129">-référence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="996bf-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="996bf-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="996bf-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
