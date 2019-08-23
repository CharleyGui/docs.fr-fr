---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 4382ec8feda2df1e83fd2fdc509abb66984e501f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937254"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="7da09-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7da09-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="7da09-103">Indique au compilateur de considérer la première occurrence d’un avertissement comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="7da09-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7da09-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7da09-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7da09-105">Arguments</span></span>  
  
|<span data-ttu-id="7da09-106">Terme</span><span class="sxs-lookup"><span data-stu-id="7da09-106">Term</span></span>|<span data-ttu-id="7da09-107">Définition</span><span class="sxs-lookup"><span data-stu-id="7da09-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="7da09-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="7da09-108">+ &#124; -</span></span>|<span data-ttu-id="7da09-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7da09-109">Optional.</span></span> <span data-ttu-id="7da09-110">Par défaut, `-warnaserror-` est en vigueur ; les avertissements n’empêchent pas le compilateur de produire un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="7da09-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="7da09-111">Du fait de l’option `-warnaserror`, qui est identique à `-warnaserror+`, les avertissements sont considérés comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="7da09-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="7da09-112">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7da09-112">Optional.</span></span> <span data-ttu-id="7da09-113">Liste délimitée par des virgules des numéros d’ID d’avertissement auxquels l’option `-warnaserror` s’applique.</span><span class="sxs-lookup"><span data-stu-id="7da09-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="7da09-114">Si aucun ID d’avertissement n’est spécifié, l’option `-warnaserror` s’applique à tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="7da09-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7da09-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7da09-115">Remarks</span></span>  
 <span data-ttu-id="7da09-116">L’option `-warnaserror` considère tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="7da09-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="7da09-117">Les messages qui d’ordinaire sont signalés comme des avertissements s’affichent en tant qu’erreurs.</span><span class="sxs-lookup"><span data-stu-id="7da09-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="7da09-118">Le compilateur signale les occurrences suivantes du même avertissement comme des avertissements.</span><span class="sxs-lookup"><span data-stu-id="7da09-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="7da09-119">Par défaut, `-warnaserror-` est en vigueur. Les avertissements sont donc uniquement à caractère informatif.</span><span class="sxs-lookup"><span data-stu-id="7da09-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="7da09-120">Du fait de l’option `-warnaserror`, qui est identique à `-warnaserror+`, les avertissements sont considérés comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="7da09-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="7da09-121">Si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="7da09-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7da09-122">L’option `-warnaserror` ne contrôle pas le mode d’affichage des avertissements.</span><span class="sxs-lookup"><span data-stu-id="7da09-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="7da09-123">Utilisez l’option [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) pour désactiver les avertissements.</span><span class="sxs-lookup"><span data-stu-id="7da09-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="7da09-124">Pour définir -warnaserror de manière à considérer tous les avertissements comme des erreurs dans l’IDE Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7da09-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7da09-125">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="7da09-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7da09-126">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7da09-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7da09-127">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="7da09-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7da09-128">3.  Vérifiez que la case **Désactiver tous les avertissements** est décochée.</span><span class="sxs-lookup"><span data-stu-id="7da09-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="7da09-129">4.  Cochez la case **Considérer tous les avertissements comme des erreurs**.</span><span class="sxs-lookup"><span data-stu-id="7da09-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="7da09-130">Pour définir -warnaserror de manière à considérer certains avertissements comme des erreurs dans l’IDE Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7da09-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7da09-131">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="7da09-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7da09-132">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7da09-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="7da09-133">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="7da09-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7da09-134">3.  Vérifiez que la case **Désactiver tous les avertissements** est décochée.</span><span class="sxs-lookup"><span data-stu-id="7da09-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="7da09-135">4.  Vérifiez que la case **Considérer tous les avertissements comme des erreurs** est décochée.</span><span class="sxs-lookup"><span data-stu-id="7da09-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="7da09-136">5.  Sélectionnez **Erreur** dans la colonne **Notification** adjacente à l’avertissement à considérer comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="7da09-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7da09-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="7da09-137">Example</span></span>  
 <span data-ttu-id="7da09-138">Le code suivant compile `In.vb` et indique au compilateur d’afficher une erreur à la première occurrence de chaque avertissement rencontré.</span><span class="sxs-lookup"><span data-stu-id="7da09-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="7da09-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="7da09-139">Example</span></span>  
 <span data-ttu-id="7da09-140">Le code suivant compile `T2.vb` et considère uniquement l’avertissement pour les variables locales inutilisées (42024) comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="7da09-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7da09-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7da09-141">See also</span></span>

- [<span data-ttu-id="7da09-142">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7da09-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7da09-143">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="7da09-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7da09-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7da09-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
