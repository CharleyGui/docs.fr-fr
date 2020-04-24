---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005212"
---
# <a name="-rootnamespace"></a><span data-ttu-id="64697-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="64697-102">-rootnamespace</span></span>
<span data-ttu-id="64697-103">Spécifie un espace de noms pour toutes les déclarations de type.</span><span class="sxs-lookup"><span data-stu-id="64697-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64697-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64697-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="64697-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64697-105">Arguments</span></span>  
  
|<span data-ttu-id="64697-106">Terme</span><span class="sxs-lookup"><span data-stu-id="64697-106">Term</span></span>|<span data-ttu-id="64697-107">Définition</span><span class="sxs-lookup"><span data-stu-id="64697-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="64697-108">Nom de l’espace de noms dans lequel placer toutes les déclarations de type pour le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="64697-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64697-109">Notes</span><span class="sxs-lookup"><span data-stu-id="64697-109">Remarks</span></span>  
 <span data-ttu-id="64697-110">Si vous utilisez le fichier exécutable Visual Studio (devenv. exe) pour compiler un projet créé dans l’environnement de développement intégré de Visual Studio, `-rootnamespace` utilisez pour spécifier la valeur de <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="64697-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="64697-111">Pour plus d’informations, consultez [commutateurs de ligne de commande devenv](/visualstudio/ide/reference/devenv-command-line-switches) .</span><span class="sxs-lookup"><span data-stu-id="64697-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="64697-112">Utilisez l’common language runtime désassembleur MSIL (`Ildasm.exe`) pour afficher les noms des espaces de noms dans votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="64697-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="64697-113">Pour Set-RootNamespace dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64697-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="64697-114">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="64697-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="64697-115">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="64697-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="64697-116">2. cliquez sur l’onglet **application** .</span><span class="sxs-lookup"><span data-stu-id="64697-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="64697-117">3. modifiez la valeur dans la zone **espace de noms racine** .</span><span class="sxs-lookup"><span data-stu-id="64697-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64697-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="64697-118">Example</span></span>  
 <span data-ttu-id="64697-119">Le code suivant compile `In.vb` et encadre toutes les déclarations de type dans l’espace de noms `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="64697-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="64697-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64697-120">See also</span></span>

- [<span data-ttu-id="64697-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64697-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="64697-122">Ildasm. exe (Désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="64697-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="64697-123">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="64697-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
