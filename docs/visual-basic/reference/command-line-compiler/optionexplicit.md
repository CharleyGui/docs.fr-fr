---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 65cc3fb1b2fa9daa04013caa2b93a3949d0a15b9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098934"
---
# <a name="-optionexplicit"></a><span data-ttu-id="5cb4d-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5cb4d-102">-optionexplicit</span></span>

<span data-ttu-id="5cb4d-103">Fait en sorte que le compilateur signale des erreurs si les variables ne sont pas déclarées avant d’être utilisées.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cb4d-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5cb4d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cb4d-105">Arguments</span></span>  

 <span data-ttu-id="5cb4d-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5cb4d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5cb4d-107">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-107">Optional.</span></span> <span data-ttu-id="5cb4d-108">Spécifiez `-optionexplicit+` pour exiger une déclaration explicite de variables.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="5cb4d-109">L' `-optionexplicit+` option est la valeur par défaut et est identique à `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="5cb4d-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="5cb4d-110">L' `-optionexplicit-` option active la déclaration implicite de variables.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cb4d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="5cb4d-111">Remarks</span></span>  

 <span data-ttu-id="5cb4d-112">Si le fichier de code source contient une [instruction Option Explicit](../../language-reference/statements/option-explicit-statement.md), l’instruction remplace le `-optionexplicit` paramètre du compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-112">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="5cb4d-113">Pour définir-optionexplicit dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cb4d-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5cb4d-114">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5cb4d-115">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="5cb4d-116">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="5cb4d-117">Modifiez la valeur dans la zone **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="5cb4d-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cb4d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="5cb4d-118">Example</span></span>  

 <span data-ttu-id="5cb4d-119">Le code suivant compile lorsque `-optionexplicit-` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5cb4d-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5cb4d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cb4d-120">See also</span></span>

- [<span data-ttu-id="5cb4d-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cb4d-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5cb4d-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="5cb4d-122">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="5cb4d-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="5cb4d-123">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="5cb4d-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5cb4d-124">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="5cb4d-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="5cb4d-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="5cb4d-126">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="5cb4d-126">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="5cb4d-127">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="5cb4d-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
