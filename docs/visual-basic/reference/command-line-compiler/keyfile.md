---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: b2084a1c0ee30478cdc9193cdfcb19476499ee93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924868"
---
# <a name="-keyfile"></a><span data-ttu-id="07318-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="07318-102">-keyfile</span></span>
<span data-ttu-id="07318-103">Spécifie un fichier contenant une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.</span><span class="sxs-lookup"><span data-stu-id="07318-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07318-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07318-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="07318-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="07318-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="07318-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="07318-106">Required.</span></span> <span data-ttu-id="07318-107">Fichier qui contient la clé.</span><span class="sxs-lookup"><span data-stu-id="07318-107">File that contains the key.</span></span> <span data-ttu-id="07318-108">Si le nom de fichier contient un espace, mettez-le entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="07318-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07318-109">Notes</span><span class="sxs-lookup"><span data-stu-id="07318-109">Remarks</span></span>  
 <span data-ttu-id="07318-110">Le compilateur insère la clé publique dans le manifeste de l’assembly, puis signe l’assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="07318-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="07318-111">Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="07318-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="07318-112">Pour plus d’informations, consultez [sn. exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="07318-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="07318-113">Si vous compilez avec `-target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="07318-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="07318-114">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="07318-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="07318-115">Utilisez [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous voulez obtenir un assembly partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="07318-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="07318-116">Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyFileAttribute>) dans le code source de n’importe quel module de langage intermédiaire Microsoft.</span><span class="sxs-lookup"><span data-stu-id="07318-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="07318-117">Si `-keyfile` et [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sont spécifiés (par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur essaie d’abord le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="07318-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="07318-118">Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="07318-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="07318-119">Si le compilateur ne trouve pas le conteneur de clé, il essaie le fichier spécifié `-keyfile`avec.</span><span class="sxs-lookup"><span data-stu-id="07318-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="07318-120">Si cela se déroule correctement, l’assembly est signé avec les informations contenues dans le fichier de clé, et les informations sur la clé sont installées dans le conteneur de clé (semblable à `sn -i`). ainsi, lors de la compilation suivante, le conteneur de clé est valide.</span><span class="sxs-lookup"><span data-stu-id="07318-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="07318-121">Notez qu’un fichier de clé peut contenir uniquement la clé publique.</span><span class="sxs-lookup"><span data-stu-id="07318-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="07318-122">Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys avec nom fort](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="07318-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07318-123">L' `-keyfile` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="07318-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07318-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="07318-124">Example</span></span>  
 <span data-ttu-id="07318-125">Le code suivant compile le fichier `Input.vb` source et spécifie un fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="07318-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="07318-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07318-126">See also</span></span>

- [<span data-ttu-id="07318-127">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="07318-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="07318-128">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07318-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="07318-129">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07318-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="07318-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="07318-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
