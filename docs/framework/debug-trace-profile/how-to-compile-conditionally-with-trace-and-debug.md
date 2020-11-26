---
title: 'Procédure : Effectuer une compilation conditionnelle avec Trace et Debug'
description: Découvrez comment effectuer une compilation conditionnelle avec les attributs conditionnels de TRACE et de débogage lors de la compilation d’une application .NET.
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
ms.openlocfilehash: 895e39593b5e84d708392d3d994267b25bc4eeea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244169"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="df7f7-103">Procédure : Effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="df7f7-103">How to: Compile Conditionally with Trace and Debug</span></span>

<span data-ttu-id="df7f7-104">Quand vous déboguez une application pendant le développement, les sorties de débogage et de traçage sont dirigées vers la fenêtre de sortie dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df7f7-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="df7f7-105">Toutefois, pour inclure les fonctionnalités de suivi dans une application déployée, vous devez compiler vos applications instrumentées en activant la directive de compilateur **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="df7f7-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="df7f7-106">De cette façon, le code de traçage peut être compilé dans la version commerciale de votre application.</span><span class="sxs-lookup"><span data-stu-id="df7f7-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="df7f7-107">Si vous n’activez pas la directive **TRACE**, tout le code de suivi est ignoré pendant la compilation et n’est pas inclus dans le code exécutable que vous déployez.</span><span class="sxs-lookup"><span data-stu-id="df7f7-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="df7f7-108">Les méthodes de traçage et de débogage sont associées à des attributs conditionnels.</span><span class="sxs-lookup"><span data-stu-id="df7f7-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="df7f7-109">Par exemple, si l’attribut conditionnel pour le suivi a la valeur **true**, toutes les instructions de suivi sont incluses dans un assembly (fichier .exe ou .dll compilé) ; si l’attribut conditionnel **Trace** a la valeur **false**, les instructions de suivi ne sont pas incluses.</span><span class="sxs-lookup"><span data-stu-id="df7f7-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="df7f7-110">Vous pouvez activer l’attribut conditionnel **Trace** ou **Debug**, les deux ou aucun pour une build.</span><span class="sxs-lookup"><span data-stu-id="df7f7-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="df7f7-111">Par conséquent, il existe quatre types de build : **Debug**, **Trace**, les deux ou aucun.</span><span class="sxs-lookup"><span data-stu-id="df7f7-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="df7f7-112">Certaines versions release pour un déploiement de production peuvent n'en contenir aucun, mais la plupart des builds contiennent les deux.</span><span class="sxs-lookup"><span data-stu-id="df7f7-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="df7f7-113">Vous pouvez spécifier les paramètres du compilateur pour votre application de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="df7f7-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="df7f7-114">Pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="df7f7-114">The property pages</span></span>  
  
- <span data-ttu-id="df7f7-115">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="df7f7-115">The command line</span></span>  
  
- <span data-ttu-id="df7f7-116">**#CONST** (pour Visual Basic) et **#define** (pour C#)</span><span class="sxs-lookup"><span data-stu-id="df7f7-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="df7f7-117">Pour modifier les paramètres de compilation dans la boîte de dialogue des pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="df7f7-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="df7f7-118">Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="df7f7-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="df7f7-119">Choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="df7f7-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="df7f7-120">En Visual Basic, cliquez sur l’onglet **Compiler** dans le volet gauche de la page de propriétés, puis sur le bouton **Options avancées de compilation** pour afficher la boîte de dialogue **Paramètres avancés du compilateur**.</span><span class="sxs-lookup"><span data-stu-id="df7f7-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="df7f7-121">Cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="df7f7-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="df7f7-122">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="df7f7-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="df7f7-123">En C#, cliquez sur l’onglet **Générer** dans le volet gauche de la page de propriétés, puis cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="df7f7-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="df7f7-124">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="df7f7-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="df7f7-125">Pour compiler du code instrumenté à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="df7f7-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="df7f7-126">Définissez un commutateur de compilateur conditionnel sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="df7f7-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="df7f7-127">Le compilateur devra contenir du code de traçage ou de débogage dans l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="df7f7-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="df7f7-128">Par exemple, l'instruction de compilateur suivante entrée sur la ligne de commande inclut le code de traçage dans un fichier exécutable compilé :</span><span class="sxs-lookup"><span data-stu-id="df7f7-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="df7f7-129">Pour Visual Basic : **vbc -r:System.dll-d :trace = true-d :debug = False MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="df7f7-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="df7f7-130">Pour C# : **csc -r:System.dll-d :trace-d :Debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="df7f7-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="df7f7-131">Pour compiler plusieurs fichiers d’application, insérez un espace entre les noms de fichiers, par exemple **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="df7f7-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="df7f7-132">La signification des directives de compilation conditionnelle utilisées dans les exemples ci-dessus est la suivante :</span><span class="sxs-lookup"><span data-stu-id="df7f7-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="df7f7-133">Directive</span><span class="sxs-lookup"><span data-stu-id="df7f7-133">Directive</span></span>|<span data-ttu-id="df7f7-134">Signification</span><span class="sxs-lookup"><span data-stu-id="df7f7-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="df7f7-135">compilateur Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df7f7-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="df7f7-136">Compilateur C#</span><span class="sxs-lookup"><span data-stu-id="df7f7-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="df7f7-137">Référence un assembly externe (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="df7f7-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="df7f7-138">Définit un symbole de compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="df7f7-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="df7f7-139">Vous devez écrire TRACE ou DEBUG en majuscules.</span><span class="sxs-lookup"><span data-stu-id="df7f7-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="df7f7-140">Pour plus d'informations sur les commandes de compilation conditionnelle, entrez `vbc /?` (pour Visual Basic) ou `csc /?` (pour C#) à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="df7f7-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="df7f7-141">Pour plus d’informations, consultez [Génération à partir de la ligne de commande](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Appel du compilateur de ligne de commande](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="df7f7-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="df7f7-142">Pour effectuer une compilation conditionnelle à l'aide de #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="df7f7-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="df7f7-143">Tapez l'instruction appropriée pour votre langage de programmation en haut du fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="df7f7-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="df7f7-144">Langage</span><span class="sxs-lookup"><span data-stu-id="df7f7-144">Language</span></span>|<span data-ttu-id="df7f7-145">.</span><span class="sxs-lookup"><span data-stu-id="df7f7-145">Statement</span></span>|<span data-ttu-id="df7f7-146">Résultats</span><span class="sxs-lookup"><span data-stu-id="df7f7-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="df7f7-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="df7f7-147">**Visual Basic**</span></span>|<span data-ttu-id="df7f7-148">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="df7f7-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="df7f7-149">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="df7f7-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="df7f7-150">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="df7f7-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="df7f7-151">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="df7f7-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="df7f7-152">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="df7f7-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="df7f7-153">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="df7f7-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="df7f7-154">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="df7f7-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="df7f7-155">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="df7f7-155">Disables debugging</span></span>|  
    |<span data-ttu-id="df7f7-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="df7f7-156">**C#**</span></span>|<span data-ttu-id="df7f7-157">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="df7f7-157">**#define TRACE**</span></span>|<span data-ttu-id="df7f7-158">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="df7f7-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="df7f7-159">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="df7f7-159">**#undef TRACE**</span></span>|<span data-ttu-id="df7f7-160">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="df7f7-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="df7f7-161">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="df7f7-161">**#define DEBUG**</span></span>|<span data-ttu-id="df7f7-162">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="df7f7-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="df7f7-163">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="df7f7-163">**#undef DEBUG**</span></span>|<span data-ttu-id="df7f7-164">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="df7f7-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="df7f7-165">Pour désactiver le traçage ou le débogage</span><span class="sxs-lookup"><span data-stu-id="df7f7-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="df7f7-166">Supprimez la directive de compilateur de votre code source.</span><span class="sxs-lookup"><span data-stu-id="df7f7-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="df7f7-167">\- ou -</span><span class="sxs-lookup"><span data-stu-id="df7f7-167">\- or -</span></span>  
  
<span data-ttu-id="df7f7-168">Commentez la directive de compilateur.</span><span class="sxs-lookup"><span data-stu-id="df7f7-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df7f7-169">Quand vous êtes prêt pour la compilation, vous pouvez choisir **Générer** dans le menu **Générer**, ou utiliser la méthode de ligne de commande, mais sans taper **d:** pour définir les symboles de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="df7f7-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7f7-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df7f7-170">See also</span></span>

- [<span data-ttu-id="df7f7-171">Traçage et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="df7f7-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="df7f7-172">Procédure : Créer, initialiser et configurer les commutateurs de trace</span><span class="sxs-lookup"><span data-stu-id="df7f7-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="df7f7-173">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="df7f7-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="df7f7-174">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="df7f7-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="df7f7-175">Procédure : Ajouter des instructions de trace dans le code d’une application</span><span class="sxs-lookup"><span data-stu-id="df7f7-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="df7f7-176">Comment : définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df7f7-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="df7f7-177">Procédure : Appeler le compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="df7f7-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
