---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347912"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="37a63-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37a63-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="37a63-103">Fait en sorte que le compilateur ne référence pas automatiquement les bibliothèques standard.</span><span class="sxs-lookup"><span data-stu-id="37a63-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37a63-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="37a63-105">Notes</span><span class="sxs-lookup"><span data-stu-id="37a63-105">Remarks</span></span>  
 <span data-ttu-id="37a63-106">L’option `-nostdlib` supprime la référence automatique à l’assembly System. dll et empêche le compilateur de lire le fichier Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="37a63-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="37a63-107">Le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe, fait référence aux assemblys .NET Framework couramment utilisés et importe les espaces de noms `System` et `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="37a63-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37a63-108">Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.</span><span class="sxs-lookup"><span data-stu-id="37a63-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37a63-109">L’option `-nostdlib` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="37a63-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37a63-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="37a63-110">Example</span></span>  
 <span data-ttu-id="37a63-111">Le code suivant compile `T2.vb` sans référencer les bibliothèques standard.</span><span class="sxs-lookup"><span data-stu-id="37a63-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="37a63-112">Vous devez définir la `_MYTYPE` constante de compilation conditionnelle sur la chaîne « Empty » pour supprimer l’objet `My`.</span><span class="sxs-lookup"><span data-stu-id="37a63-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="37a63-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37a63-113">See also</span></span>

- [<span data-ttu-id="37a63-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="37a63-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="37a63-115">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37a63-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="37a63-116">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="37a63-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="37a63-117">Personnalisation de la disponibilité ou non des objets dans My</span><span class="sxs-lookup"><span data-stu-id="37a63-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
