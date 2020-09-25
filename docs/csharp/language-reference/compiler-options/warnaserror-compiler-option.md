---
description: -warnaserror (Options du compilateur C#)
title: -warnaserror (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 9c3b307668968865b401aedc04c79f95d4f32513
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171336"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="a4adb-103">-warnaserror (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="a4adb-103">-warnaserror (C# Compiler Options)</span></span>

<span data-ttu-id="a4adb-104">L’option **-warnaserror+** considère tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="a4adb-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4adb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4adb-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="a4adb-106">Notes</span><span class="sxs-lookup"><span data-stu-id="a4adb-106">Remarks</span></span>  

 <span data-ttu-id="a4adb-107">Les messages qui d’ordinaire auraient été signalés comme des avertissements s’affichent en tant qu’erreurs, et le processus de génération est arrêté (aucun fichier de sortie n’est généré).</span><span class="sxs-lookup"><span data-stu-id="a4adb-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="a4adb-108">Comme **-warnaserror** est activé par défaut, les avertissements n’empêchent pas la génération d’un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="a4adb-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="a4adb-109">Du fait de **-warnaserror**, qui est identique à **-warnaserror+**, les avertissements sont considérés comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="a4adb-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="a4adb-110">Le cas échéant, si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="a4adb-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="a4adb-111">Le jeu de tous les avertissements de possibilité de valeur NULL peut être spécifié avec le raccourci **Nullable** .</span><span class="sxs-lookup"><span data-stu-id="a4adb-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="a4adb-112">Utilisez [-warn](./warn-compiler-option.md) pour spécifier le niveau des avertissements que le compilateur doit afficher.</span><span class="sxs-lookup"><span data-stu-id="a4adb-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="a4adb-113">Utilisez [-nowarn](./nowarn-compiler-option.md) pour désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="a4adb-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a4adb-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a4adb-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a4adb-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="a4adb-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a4adb-116">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="a4adb-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a4adb-117">Modifiez la propriété **Considérer les avertissements comme des erreurs**.</span><span class="sxs-lookup"><span data-stu-id="a4adb-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="a4adb-118">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="a4adb-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4adb-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4adb-119">Example</span></span>  

 <span data-ttu-id="a4adb-120">Compilez `in.cs` et faites en sorte que le compilateur n’affiche aucun avertissement :</span><span class="sxs-lookup"><span data-stu-id="a4adb-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4adb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4adb-121">See also</span></span>

- [<span data-ttu-id="a4adb-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="a4adb-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a4adb-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="a4adb-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
