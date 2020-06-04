---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 31b719fb7e43cdd6ac44424b359999410dd608a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403042"
---
# <a name="-vbruntime"></a><span data-ttu-id="1e4d2-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="1e4d2-102">-vbruntime</span></span>
<span data-ttu-id="1e4d2-103">Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e4d2-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e4d2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e4d2-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="1e4d2-106">Compilez sans référence à la bibliothèque Runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="1e4d2-107">Compilez avec une référence à la bibliothèque Visual Basic Runtime par défaut.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="1e4d2-108">Compilez sans une référence à la bibliothèque Runtime Visual Basic et incorporez les fonctionnalités principales de la bibliothèque Visual Basic Runtime dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="1e4d2-109">Compilez avec une référence à la bibliothèque (DLL) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e4d2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-110">Remarks</span></span>  
 <span data-ttu-id="1e4d2-111">L' `-vbruntime` option de compilateur vous permet de spécifier que le compilateur doit compiler sans référence à la bibliothèque d’exécution Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="1e4d2-112">Si vous compilez sans une référence à la bibliothèque Runtime Visual Basic, des erreurs ou des avertissements sont enregistrés dans les constructions de code ou de langage qui génèrent un appel à une application auxiliaire Visual Basic Runtime.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="1e4d2-113">(Une *Visual Basic Helper du runtime* est une fonction définie dans Microsoft. VisualBasic. dll qui est appelée au moment de l’exécution pour exécuter une sémantique de langage spécifique.)</span><span class="sxs-lookup"><span data-stu-id="1e4d2-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="1e4d2-114">L' `-vbruntime+` option produit le même comportement qui se produit si aucun `-vbruntime` commutateur n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="1e4d2-115">Vous pouvez utiliser l' `-vbruntime+` option pour remplacer les `-vbruntime` commutateurs précédents.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="1e4d2-116">La plupart des objets du `My` type ne sont pas disponibles lorsque vous utilisez les `-vbruntime-` `-vbruntime:path` options ou.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="1e4d2-117">Incorporation des fonctionnalités principales du runtime d’Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e4d2-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="1e4d2-118">L' `-vbruntime*` option vous permet de compiler sans référence à une bibliothèque Runtime.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="1e4d2-119">Au lieu de cela, les fonctionnalités principales de la bibliothèque Runtime Visual Basic sont incorporées dans l’assembly utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="1e4d2-120">Vous pouvez utiliser cette option si votre application s’exécute sur des plateformes qui ne contiennent pas le runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="1e4d2-121">Les membres du runtime suivants sont incorporés :</span><span class="sxs-lookup"><span data-stu-id="1e4d2-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="1e4d2-122">Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="1e4d2-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="1e4d2-123">Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="1e4d2-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="1e4d2-124">Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="1e4d2-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="1e4d2-125">Méthode <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="1e4d2-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="1e4d2-126"><xref:Microsoft.VisualBasic.Constants.vbBack>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="1e4d2-127"><xref:Microsoft.VisualBasic.Constants.vbCr>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="1e4d2-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="1e4d2-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="1e4d2-130"><xref:Microsoft.VisualBasic.Constants.vbLf>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="1e4d2-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="1e4d2-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="1e4d2-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="1e4d2-134"><xref:Microsoft.VisualBasic.Constants.vbTab>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="1e4d2-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>suivantes</span><span class="sxs-lookup"><span data-stu-id="1e4d2-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="1e4d2-136">Certains objets du `My` type</span><span class="sxs-lookup"><span data-stu-id="1e4d2-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="1e4d2-137">Si vous compilez à l’aide de l' `-vbruntime*` option et que votre code fait référence à un membre de la bibliothèque d’exécution Visual Basic qui n’est pas incorporée avec la fonctionnalité de base, le compilateur retourne une erreur qui indique que le membre n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="1e4d2-138">Référencement d’une bibliothèque spécifiée</span><span class="sxs-lookup"><span data-stu-id="1e4d2-138">Referencing a specified library</span></span>  
 <span data-ttu-id="1e4d2-139">Vous pouvez utiliser l' `path` argument pour compiler avec une référence à une bibliothèque Runtime personnalisée au lieu de la bibliothèque Visual Basic Runtime par défaut.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="1e4d2-140">Si la valeur de l' `path` argument est un chemin d’accès qualifié complet à une dll, le compilateur utilise ce fichier comme bibliothèque Runtime.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="1e4d2-141">Si la valeur de l' `path` argument n’est pas un chemin d’accès complet à une dll, le compilateur Visual Basic recherche d’abord la DLL identifiée dans le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="1e4d2-142">Il effectue ensuite une recherche dans le chemin d’accès que vous avez spécifié à l’aide de l’option [de compilateur-sdkpath](sdkpath.md) .</span><span class="sxs-lookup"><span data-stu-id="1e4d2-142">It will then search in the path that you have specified by using the [-sdkpath](sdkpath.md) compiler option.</span></span> <span data-ttu-id="1e4d2-143">Si l' `-sdkpath` option de compilateur n’est pas utilisée, le compilateur recherche la DLL identifiée dans le dossier .NET Framework ( `%systemroot%\Microsoft.NET\Framework\versionNumber` ).</span><span class="sxs-lookup"><span data-stu-id="1e4d2-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4d2-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e4d2-144">Example</span></span>  
 <span data-ttu-id="1e4d2-145">L’exemple suivant montre comment utiliser l' `-vbruntime` option pour compiler avec une référence à une bibliothèque personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1e4d2-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e4d2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e4d2-146">See also</span></span>

- [<span data-ttu-id="1e4d2-147">Visual Basic Core – nouveau mode de compilation dans Visual Studio 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="1e4d2-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="1e4d2-148">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e4d2-148">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1e4d2-149">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="1e4d2-149">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="1e4d2-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="1e4d2-150">-sdkpath</span></span>](sdkpath.md)
