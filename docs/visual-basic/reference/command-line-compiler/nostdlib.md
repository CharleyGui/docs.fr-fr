---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4fcc5305985f5ba32b3e6ffb740c0611821215d3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097655"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="e4fe8-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4fe8-102">-nostdlib (Visual Basic)</span></span>

<span data-ttu-id="e4fe8-103">Fait en sorte que le compilateur ne référence pas automatiquement les bibliothèques standard.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4fe8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4fe8-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4fe8-105">Notes</span><span class="sxs-lookup"><span data-stu-id="e4fe8-105">Remarks</span></span>  

 <span data-ttu-id="e4fe8-106">L' `-nostdlib` option supprime la référence automatique à l’assembly System.dll et empêche le compilateur de lire le fichier Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="e4fe8-107">Le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe, fait référence aux assemblys de .NET Framework couramment utilisés et importe les `System` `Microsoft.VisualBasic` espaces de noms et.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4fe8-108">Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4fe8-109">L' `-nostdlib` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4fe8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4fe8-110">Example</span></span>  

 <span data-ttu-id="e4fe8-111">Le code suivant compile `T2.vb` sans référencer les bibliothèques standard.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="e4fe8-112">Vous devez définir la `_MYTYPE` constante de compilation conditionnelle sur la chaîne « Empty » pour supprimer l' `My` objet.</span><span class="sxs-lookup"><span data-stu-id="e4fe8-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4fe8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4fe8-113">See also</span></span>

- [<span data-ttu-id="e4fe8-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e4fe8-114">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="e4fe8-115">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4fe8-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e4fe8-116">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e4fe8-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="e4fe8-117">Personnalisation de la disponibilité ou non des objets dans My</span><span class="sxs-lookup"><span data-stu-id="e4fe8-117">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
