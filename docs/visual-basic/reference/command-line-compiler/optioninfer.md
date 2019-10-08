---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: c6fc7e9dcfbce938ad75b0f357c2bfa9cd10703a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005325"
---
# <a name="-optioninfer"></a><span data-ttu-id="3c5c1-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3c5c1-102">-optioninfer</span></span>
<span data-ttu-id="3c5c1-103">Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c5c1-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c5c1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3c5c1-105">Arguments</span></span>  
  
|<span data-ttu-id="3c5c1-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3c5c1-106">Term</span></span>|<span data-ttu-id="3c5c1-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3c5c1-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3c5c1-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3c5c1-108">`+` &#124; `-`</span></span>|<span data-ttu-id="3c5c1-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-109">Optional.</span></span> <span data-ttu-id="3c5c1-110">Spécifiez `-optioninfer+` pour activer l'inférence de type de variable locale ou `-optioninfer-` pour la bloquer.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="3c5c1-111">L'option `-optioninfer`, sans aucune valeur spécifiée, est identique à `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="3c5c1-112">La valeur par défaut en l'absence du commutateur `-optioninfer` est aussi `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="3c5c1-113">La valeur par défaut est définie dans le fichier réponse Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3c5c1-114">Vous pouvez utiliser l'option `-noconfig` pour conserver les valeurs par défaut internes du compilateur au lieu de celles spécifiées dans le fichier vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="3c5c1-115">Pour cette option, la valeur par défaut du compilateur est `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5c1-116">Notes</span><span class="sxs-lookup"><span data-stu-id="3c5c1-116">Remarks</span></span>  
 <span data-ttu-id="3c5c1-117">Si le fichier de code source contient une [instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md), l’instruction remplace le paramètre du compilateur de ligne de commande `-optioninfer`.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="3c5c1-118">Pour définir-optioninfer (dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3c5c1-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="3c5c1-119">Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="3c5c1-120">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="3c5c1-121">Sous l’onglet **compiler** , modifiez la valeur dans la zone **Option Infer** .</span><span class="sxs-lookup"><span data-stu-id="3c5c1-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c5c1-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c5c1-122">Example</span></span>  
 <span data-ttu-id="3c5c1-123">Le code suivant compile `test.vb` avec l'inférence de type de variable locale activée.</span><span class="sxs-lookup"><span data-stu-id="3c5c1-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c5c1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c5c1-124">See also</span></span>

- [<span data-ttu-id="3c5c1-125">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c5c1-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3c5c1-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3c5c1-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3c5c1-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3c5c1-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="3c5c1-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3c5c1-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="3c5c1-129">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3c5c1-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3c5c1-130">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5c1-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3c5c1-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="3c5c1-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3c5c1-132">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="3c5c1-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="3c5c1-133">Page Compiler, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c5c1-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="3c5c1-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="3c5c1-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="3c5c1-135">Génération à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3c5c1-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
