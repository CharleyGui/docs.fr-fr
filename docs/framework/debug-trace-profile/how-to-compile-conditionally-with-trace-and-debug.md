---
title: 'Comment : effectuer une compilation conditionnelle avec Trace et Debug'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2cb2ef473d6870da47e0e4c00fecf6bd60707f3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975582"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="741da-102">Comment : effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="741da-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="741da-103">Quand vous déboguez une application pendant le développement, les sorties de débogage et de traçage sont dirigées vers la fenêtre de sortie dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="741da-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="741da-104">Toutefois, pour inclure les fonctionnalités de suivi dans une application déployée, vous devez compiler vos applications instrumentées en activant la directive de compilateur **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="741da-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="741da-105">De cette façon, le code de traçage peut être compilé dans la version commerciale de votre application.</span><span class="sxs-lookup"><span data-stu-id="741da-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="741da-106">Si vous n’activez pas la directive **TRACE**, tout le code de suivi est ignoré pendant la compilation et n’est pas inclus dans le code exécutable que vous déployez.</span><span class="sxs-lookup"><span data-stu-id="741da-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="741da-107">Les méthodes de traçage et de débogage sont associées à des attributs conditionnels.</span><span class="sxs-lookup"><span data-stu-id="741da-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="741da-108">Par exemple, si l’attribut conditionnel pour le suivi a la valeur **true**, toutes les instructions de suivi sont incluses dans un assembly (fichier .exe ou .dll compilé) ; si l’attribut conditionnel **Trace** a la valeur **false**, les instructions de suivi ne sont pas incluses.</span><span class="sxs-lookup"><span data-stu-id="741da-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="741da-109">Vous pouvez activer l’attribut conditionnel **Trace** ou **Debug**, les deux ou aucun pour une build.</span><span class="sxs-lookup"><span data-stu-id="741da-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="741da-110">Par conséquent, il existe quatre types de build : **Debug**, **Trace**, les deux ou aucun.</span><span class="sxs-lookup"><span data-stu-id="741da-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="741da-111">Certaines versions release pour un déploiement de production peuvent n'en contenir aucun, mais la plupart des builds contiennent les deux.</span><span class="sxs-lookup"><span data-stu-id="741da-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="741da-112">Vous pouvez spécifier les paramètres du compilateur pour votre application de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="741da-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="741da-113">Pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="741da-113">The property pages</span></span>  
  
- <span data-ttu-id="741da-114">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="741da-114">The command line</span></span>  
  
- <span data-ttu-id="741da-115">**#CONST** (pour Visual Basic) et **#define** (pour C#)</span><span class="sxs-lookup"><span data-stu-id="741da-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="741da-116">Pour modifier les paramètres de compilation dans la boîte de dialogue des pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="741da-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="741da-117">Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="741da-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="741da-118">Choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="741da-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="741da-119">En Visual Basic, cliquez sur l’onglet **Compiler** dans le volet gauche de la page de propriétés, puis sur le bouton **Options avancées de compilation** pour afficher la boîte de dialogue **Paramètres avancés du compilateur**.</span><span class="sxs-lookup"><span data-stu-id="741da-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="741da-120">Cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="741da-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="741da-121">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="741da-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="741da-122">En C#, cliquez sur l’onglet **Générer** dans le volet gauche de la page de propriétés, puis cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="741da-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="741da-123">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="741da-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="741da-124">Pour compiler du code instrumenté à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="741da-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="741da-125">Définissez un commutateur de compilateur conditionnel sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="741da-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="741da-126">Le compilateur devra contenir du code de traçage ou de débogage dans l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="741da-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="741da-127">Par exemple, l'instruction de compilateur suivante entrée sur la ligne de commande inclut le code de traçage dans un fichier exécutable compilé :</span><span class="sxs-lookup"><span data-stu-id="741da-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="741da-128">Pour Visual Basic : **vbc-r :System.dll-d :trace = true-d :debug = False MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="741da-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="741da-129">Pour C#: **csc-r :System.dll-d :trace-d :debug = False MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="741da-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="741da-130">Pour compiler plusieurs fichiers d’application, insérez un espace entre les noms de fichiers, par exemple **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="741da-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="741da-131">La signification des directives de compilation conditionnelle utilisées dans les exemples ci-dessus est la suivante :</span><span class="sxs-lookup"><span data-stu-id="741da-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="741da-132">Directive</span><span class="sxs-lookup"><span data-stu-id="741da-132">Directive</span></span>|<span data-ttu-id="741da-133">Signification</span><span class="sxs-lookup"><span data-stu-id="741da-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="741da-134">compilateur Visual Basic</span><span class="sxs-lookup"><span data-stu-id="741da-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="741da-135">Compilateur C#</span><span class="sxs-lookup"><span data-stu-id="741da-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="741da-136">Référence un assembly externe (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="741da-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="741da-137">Définit un symbole de compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="741da-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="741da-138">Vous devez écrire TRACE ou DEBUG en majuscules.</span><span class="sxs-lookup"><span data-stu-id="741da-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="741da-139">Pour plus d'informations sur les commandes de compilation conditionnelle, entrez `vbc /?` (pour Visual Basic) ou `csc /?` (pour C#) à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="741da-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="741da-140">Pour plus d’informations, consultez [Génération à partir de la ligne de commande](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Appel du compilateur de ligne de commande](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="741da-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="741da-141">Pour effectuer une compilation conditionnelle à l'aide de #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="741da-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="741da-142">Tapez l'instruction appropriée pour votre langage de programmation en haut du fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="741da-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="741da-143">Langue</span><span class="sxs-lookup"><span data-stu-id="741da-143">Language</span></span>|<span data-ttu-id="741da-144">Instruction</span><span class="sxs-lookup"><span data-stu-id="741da-144">Statement</span></span>|<span data-ttu-id="741da-145">Résultat</span><span class="sxs-lookup"><span data-stu-id="741da-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="741da-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="741da-146">**Visual Basic**</span></span>|<span data-ttu-id="741da-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="741da-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="741da-148">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="741da-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="741da-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="741da-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="741da-150">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="741da-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="741da-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="741da-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="741da-152">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="741da-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="741da-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="741da-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="741da-154">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="741da-154">Disables debugging</span></span>|  
    |<span data-ttu-id="741da-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="741da-155">**C#**</span></span>|<span data-ttu-id="741da-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="741da-156">**#define TRACE**</span></span>|<span data-ttu-id="741da-157">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="741da-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="741da-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="741da-158">**#undef TRACE**</span></span>|<span data-ttu-id="741da-159">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="741da-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="741da-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="741da-160">**#define DEBUG**</span></span>|<span data-ttu-id="741da-161">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="741da-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="741da-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="741da-162">**#undef DEBUG**</span></span>|<span data-ttu-id="741da-163">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="741da-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="741da-164">Pour désactiver le traçage ou le débogage</span><span class="sxs-lookup"><span data-stu-id="741da-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="741da-165">Supprimez la directive de compilateur de votre code source.</span><span class="sxs-lookup"><span data-stu-id="741da-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="741da-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="741da-166">\- or -</span></span>  
  
<span data-ttu-id="741da-167">Commentez la directive de compilateur.</span><span class="sxs-lookup"><span data-stu-id="741da-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="741da-168">Quand vous êtes prêt pour la compilation, vous pouvez choisir **Générer** dans le menu **Générer**, ou utiliser la méthode de ligne de commande, mais sans taper **d:** pour définir les symboles de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="741da-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741da-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="741da-169">See also</span></span>

- [<span data-ttu-id="741da-170">Suivi et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="741da-170">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="741da-171">Guide pratique pour créer, initialiser et configurer des commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="741da-171">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="741da-172">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="741da-172">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="741da-173">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="741da-173">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="741da-174">Guide pratique pour ajouter des instructions de suivi au code d’application</span><span class="sxs-lookup"><span data-stu-id="741da-174">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="741da-175">Comment définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="741da-175">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="741da-176">Guide pratique : appeler le compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="741da-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
