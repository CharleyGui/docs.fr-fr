---
description: -doc (Options du compilateur C#)
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
ms.openlocfilehash: b1d7fbbe98aaad16454fdd71c161f2a17a2f4f2e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173254"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="f9181-103">-doc (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f9181-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="f9181-104">L’option **-doc** vous permet de placer des commentaires de documentation dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="f9181-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9181-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9181-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9181-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f9181-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="f9181-107">Fichier de sortie XML, qui est rempli avec les commentaires des fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f9181-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9181-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f9181-108">Remarks</span></span>  

 <span data-ttu-id="f9181-109">Dans les fichiers de code source, les commentaires de documentation qui précèdent les éléments suivants peuvent être traités et ajoutés au fichier XML :</span><span class="sxs-lookup"><span data-stu-id="f9181-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="f9181-110">Types définis par l’utilisateur, tels qu’une [classe](../keywords/class.md), un [délégué](../builtin-types/reference-types.md#the-delegate-type) ou une [interface](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="f9181-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="f9181-111">Membres tels qu’un champ, un [événement](../keywords/event.md), une [propriété](../../programming-guide/classes-and-structs/using-properties.md) ou une méthode</span><span class="sxs-lookup"><span data-stu-id="f9181-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="f9181-112">Le fichier de code source qui contient Main est sorti en premier dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="f9181-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="f9181-113">Pour utiliser le fichier .xml généré avec la fonctionnalité [IntelliSense](/visualstudio/ide/using-intellisense), faites en sorte que le nom du fichier .xml soit identique à l’assembly que vous souhaitez prendre en charge, puis vérifiez que le fichier .xml est dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f9181-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="f9181-114">Ainsi, quand l’assembly est référencé dans le projet Visual Studio, le fichier .xml est également trouvé.</span><span class="sxs-lookup"><span data-stu-id="f9181-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="f9181-115">Pour plus d’informations, consultez [Insertion de commentaires dans le code XML](/visualstudio/ide/reference/generate-xml-documentation-comments).</span><span class="sxs-lookup"><span data-stu-id="f9181-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="f9181-116">Sauf si vous compilez avec [-target : module](./target-module-compiler-option.md), `file` contient des \<assembly> \</assembly> balises qui spécifient le nom du fichier contenant le manifeste d’assembly pour le fichier de sortie de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f9181-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9181-117">L’option -doc s’applique à tous les fichiers d’entrée ou, si elle est définie dans les paramètres de projet, à tous les fichiers du projet.</span><span class="sxs-lookup"><span data-stu-id="f9181-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="f9181-118">Pour désactiver les avertissements relatifs aux commentaires de documentation pour un fichier ou une section de code spécifique, utilisez [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="f9181-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="f9181-119">Pour découvrir comment générer de la documentation à partir de commentaires dans votre code, consultez [Balises recommandées pour les commentaires de documentation](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="f9181-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f9181-120">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9181-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f9181-121">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="f9181-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f9181-122">Cliquez sur l’onglet **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f9181-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="f9181-123">Modifiez la propriété **Fichier de documentation XML**.</span><span class="sxs-lookup"><span data-stu-id="f9181-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="f9181-124">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9181-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9181-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9181-125">See also</span></span>

- [<span data-ttu-id="f9181-126">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="f9181-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f9181-127">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f9181-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
