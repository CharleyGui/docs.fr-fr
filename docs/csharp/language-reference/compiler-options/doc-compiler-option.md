---
title: -doc (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: 7c8fc11c8799912ea6340940ccd254ae82519591
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591690"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="75466-102">-doc (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="75466-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="75466-103">L’option **-doc** vous permet de placer des commentaires de documentation dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="75466-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75466-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75466-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="75466-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="75466-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="75466-106">Fichier de sortie XML, qui est rempli avec les commentaires des fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="75466-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75466-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="75466-107">Remarks</span></span>  
 <span data-ttu-id="75466-108">Dans les fichiers de code source, les commentaires de documentation qui précèdent les éléments suivants peuvent être traités et ajoutés au fichier XML :</span><span class="sxs-lookup"><span data-stu-id="75466-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="75466-109">Types définis par l’utilisateur, tels qu’une [classe](../../../csharp/language-reference/keywords/class.md), un [délégué](../../../csharp/language-reference/keywords/delegate.md) ou une [interface](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="75466-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
- <span data-ttu-id="75466-110">Membres tels qu’un champ, un [événement](../../../csharp/language-reference/keywords/event.md), une [propriété](../../../csharp/programming-guide/classes-and-structs/using-properties.md) ou une méthode</span><span class="sxs-lookup"><span data-stu-id="75466-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="75466-111">Le fichier de code source qui contient Main est sorti en premier dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="75466-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="75466-112">Pour utiliser le fichier .xml généré avec la fonctionnalité [IntelliSense](/visualstudio/ide/using-intellisense), faites en sorte que le nom du fichier .xml soit identique à l’assembly que vous souhaitez prendre en charge, puis vérifiez que le fichier .xml est dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="75466-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="75466-113">Ainsi, quand l’assembly est référencé dans le projet Visual Studio, le fichier .xml est également trouvé.</span><span class="sxs-lookup"><span data-stu-id="75466-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="75466-114">Pour plus d’informations, consultez [Insertion de commentaires dans le code XML](/visualstudio/ide/supplying-xml-code-comments).</span><span class="sxs-lookup"><span data-stu-id="75466-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="75466-115">Sauf si vous compilez avec [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` contiendra des balises \<assembly>\<-assembly> spécifiant le nom du fichier qui contient le manifeste d’assembly pour le fichier de sortie de la compilation.</span><span class="sxs-lookup"><span data-stu-id="75466-115">Unless you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75466-116">L’option -doc s’applique à tous les fichiers d’entrée ou, si elle est définie dans les paramètres de projet, à tous les fichiers du projet.</span><span class="sxs-lookup"><span data-stu-id="75466-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="75466-117">Pour désactiver les avertissements relatifs aux commentaires de documentation pour un fichier ou une section de code spécifique, utilisez [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="75466-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="75466-118">Pour découvrir comment générer de la documentation à partir de commentaires dans votre code, consultez [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="75466-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="75466-119">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75466-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="75466-120">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="75466-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="75466-121">Cliquez sur l’onglet **Générer**.</span><span class="sxs-lookup"><span data-stu-id="75466-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="75466-122">Modifiez la propriété **Fichier de documentation XML**.</span><span class="sxs-lookup"><span data-stu-id="75466-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="75466-123">Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="75466-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75466-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75466-124">See also</span></span>

- [<span data-ttu-id="75466-125">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="75466-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="75466-126">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="75466-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
