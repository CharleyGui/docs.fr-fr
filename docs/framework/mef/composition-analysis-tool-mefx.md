---
title: Outil d'analyse de la composition (Mefx)
description: En savoir plus sur l’outil d’analyse de composition (Mefx), qui analyse les fichiers DLL et EXE qui contiennent des parties Managed Extensibility Framework (MEF) dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: abb1459afc5aeb2d39ee553c62fe382bb7af58d5
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281275"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="a3bef-103">Outil d'analyse de la composition (Mefx)</span><span class="sxs-lookup"><span data-stu-id="a3bef-103">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="a3bef-104">L'outil d'analyse de composition (Mefx) est une application en ligne de commande qui analyse les fichiers de bibliothèque (.dll) et d'application (.exe) contenant des éléments de Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="a3bef-104">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="a3bef-105">L'objectif principal de Mefx est d'offrir aux développeurs un moyen de diagnostiquer les échecs de composition dans leurs applications MEF sans avoir à ajouter du code de traçage encombrant à l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="a3bef-105">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="a3bef-106">Il peut également permettre de comprendre les éléments d'une bibliothèque fournie par un tiers.</span><span class="sxs-lookup"><span data-stu-id="a3bef-106">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="a3bef-107">Cette rubrique explique comment utiliser Mefx et fournit une référence pour sa syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a3bef-107">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="a3bef-108">Obtention de Mefx</span><span class="sxs-lookup"><span data-stu-id="a3bef-108">Getting Mefx</span></span>  
 <span data-ttu-id="a3bef-109">Mefx est disponible sur GitHub à l’adresse [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="a3bef-109">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="a3bef-110">Il vous suffit de télécharger l'outil et de le décompresser.</span><span class="sxs-lookup"><span data-stu-id="a3bef-110">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="a3bef-111">Syntaxe de base</span><span class="sxs-lookup"><span data-stu-id="a3bef-111">Basic Syntax</span></span>  
 <span data-ttu-id="a3bef-112">Mefx est appelé à partir de la ligne de commande au format suivant :</span><span class="sxs-lookup"><span data-stu-id="a3bef-112">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="a3bef-113">Le premier jeu d'arguments spécifie les fichiers et répertoires à partir desquels charger les éléments à analyser.</span><span class="sxs-lookup"><span data-stu-id="a3bef-113">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="a3bef-114">Spécifiez un fichier avec le commutateur `/file:` et un répertoire avec le commutateur `/directory:` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-114">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="a3bef-115">Vous pouvez spécifier plusieurs fichiers ou répertoires, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a3bef-115">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="a3bef-116">Chaque .dll ou .exe ne doit être chargé qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a3bef-116">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="a3bef-117">Si un fichier est chargé plusieurs fois, l'outil peut retourner des informations incorrectes.</span><span class="sxs-lookup"><span data-stu-id="a3bef-117">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="a3bef-118">Une fois dressée la liste des fichiers et des répertoires, vous devez spécifier une commande ainsi que toutes les options de cette commande.</span><span class="sxs-lookup"><span data-stu-id="a3bef-118">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="a3bef-119">Liste des éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="a3bef-119">Listing Available Parts</span></span>  
 <span data-ttu-id="a3bef-120">Utilisez l'action `/parts` pour répertorier tous les éléments déclarés dans les fichiers chargés.</span><span class="sxs-lookup"><span data-stu-id="a3bef-120">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="a3bef-121">Le résultat est une simple liste de noms d'éléments.</span><span class="sxs-lookup"><span data-stu-id="a3bef-121">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="a3bef-122">Pour plus d'informations sur les éléments, utilisez l'option `/verbose` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-122">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="a3bef-123">Vous obtiendrez ainsi plus d'informations pour tous les éléments disponibles.</span><span class="sxs-lookup"><span data-stu-id="a3bef-123">This will output more information for all available parts.</span></span> <span data-ttu-id="a3bef-124">Pour obtenir plus d'informations sur un seul élément, utilisez l'action `/type` au lieu de `/parts`.</span><span class="sxs-lookup"><span data-stu-id="a3bef-124">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="a3bef-125">Liste des importations et exportations</span><span class="sxs-lookup"><span data-stu-id="a3bef-125">Listing Imports and Exports</span></span>  
 <span data-ttu-id="a3bef-126">Les actions `/imports` et `/exports` répertorient tous les éléments importés et exportés, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a3bef-126">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="a3bef-127">Vous pouvez également répertorier les éléments qui importent ou exportent un type particulier à l'aide des actions `/importers` ou `/exporters` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-127">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="a3bef-128">Vous pouvez également appliquer l'option `/verbose` à ces actions.</span><span class="sxs-lookup"><span data-stu-id="a3bef-128">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="a3bef-129">Recherche d'éléments rejetés</span><span class="sxs-lookup"><span data-stu-id="a3bef-129">Finding Rejected Parts</span></span>  
 <span data-ttu-id="a3bef-130">Une fois que Mefx a chargé les éléments disponibles, il utilise le moteur de composition MEF pour les composer.</span><span class="sxs-lookup"><span data-stu-id="a3bef-130">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="a3bef-131">Les éléments qui ne peuvent pas être correctement composés sont les éléments *rejetés*.</span><span class="sxs-lookup"><span data-stu-id="a3bef-131">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="a3bef-132">Pour répertorier tous les éléments rejetés, utilisez l'action `/rejected` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-132">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="a3bef-133">Vous pouvez utiliser l'option `/verbose` avec l'action `/rejected` pour imprimer des informations détaillées sur les éléments rejetés.</span><span class="sxs-lookup"><span data-stu-id="a3bef-133">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="a3bef-134">Dans l'exemple suivant, la DLL `ClassLibrary1` contient l'élément `AddIn` , qui importe les éléments `MemberPart` et `ChainOne` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-134">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="a3bef-135">`ChainOne` importe `ChainTwo`, mais `ChainTwo` n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a3bef-135">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="a3bef-136">Cela signifie que `ChainOne` est rejeté, ce qui conduit au rejet de l'élément `AddIn` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-136">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="a3bef-137">Voici la sortie complète de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="a3bef-137">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="a3bef-138">Les informations intéressantes sont contenues dans les résultats `[Exception]` et `[Unsuitable]` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-138">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="a3bef-139">Le résultat `[Exception]` fournit des informations sur les raisons du rejet d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a3bef-139">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="a3bef-140">Le résultat `[Unsuitable]` indique les raisons pour lesquelles un élément qui devrait correspondre ne peut pas servir à remplir une importation. Dans ce cas, c'est parce que cet élément a lui-même été rejeté en raison d'importations manquantes.</span><span class="sxs-lookup"><span data-stu-id="a3bef-140">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="a3bef-141">Analyse des causes principales</span><span class="sxs-lookup"><span data-stu-id="a3bef-141">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="a3bef-142">Si plusieurs éléments sont liés dans une longue chaîne de dépendance, un problème impliquant un élément vers le bas peut entraîner le rejet de la chaîne entière.</span><span class="sxs-lookup"><span data-stu-id="a3bef-142">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="a3bef-143">Le diagnostic de ces problèmes peut être difficile, car la cause première de l'échec n'est pas toujours évidente.</span><span class="sxs-lookup"><span data-stu-id="a3bef-143">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="a3bef-144">Pour résoudre le problème, vous pouvez utiliser l'action `/causes` , qui tente de trouver la cause première d'un rejet en cascade.</span><span class="sxs-lookup"><span data-stu-id="a3bef-144">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="a3bef-145">L'utilisation de l'action `/causes` sur l'exemple précédent indique uniquement les informations relatives à `ChainOne`, dont l'importation vide est la cause première du rejet de `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="a3bef-145">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="a3bef-146">L'action `/causes` peut être utilisée dans les options normales et `/verbose` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-146">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3bef-147">Dans la plupart des cas, Mefx peut diagnostiquer la cause première d'un échec en cascade.</span><span class="sxs-lookup"><span data-stu-id="a3bef-147">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="a3bef-148">Toutefois, dans les cas où des éléments sont ajoutés par programmation à un conteneur, les cas impliquant des conteneurs hiérarchiques ou des implémentations `ExportProvider` personnalisées, Mefx ne peut pas diagnostiquer la cause.</span><span class="sxs-lookup"><span data-stu-id="a3bef-148">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="a3bef-149">En général, les cas décrits précédemment doivent être évités autant que possible, car les échecs sont généralement difficiles à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="a3bef-149">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="a3bef-150">Listes vertes</span><span class="sxs-lookup"><span data-stu-id="a3bef-150">White Lists</span></span>  
 <span data-ttu-id="a3bef-151">L'option `/whitelist` vous permet de spécifier un fichier texte qui répertorie les éléments devant être rejetés.</span><span class="sxs-lookup"><span data-stu-id="a3bef-151">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="a3bef-152">Les rejets inattendus seront alors signalés.</span><span class="sxs-lookup"><span data-stu-id="a3bef-152">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="a3bef-153">Cela peut être utile quand vous analysez une bibliothèque incomplète ou qu'une sous-bibliothèque ne contient pas toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="a3bef-153">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="a3bef-154">L'option `/whitelist` peut être appliquée aux actions `/rejected` ou `/causes` .</span><span class="sxs-lookup"><span data-stu-id="a3bef-154">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="a3bef-155">Supposons un fichier nommé test.txt contenant le texte « ClassLibrary1.ChainOne ».</span><span class="sxs-lookup"><span data-stu-id="a3bef-155">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="a3bef-156">Si vous exécutez l'action `/rejected` avec l'option `/whitelist` sur l'exemple précédent, vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a3bef-156">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
