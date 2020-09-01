---
description: -define (Options du compilateur C#)
title: -define (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125876"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="79156-103">-define (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="79156-103">-define (C# Compiler Options)</span></span>
<span data-ttu-id="79156-104">L’option **-define** définit `name` comme symbole dans tous les fichiers de code source de votre programme.</span><span class="sxs-lookup"><span data-stu-id="79156-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79156-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79156-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="79156-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="79156-106">Arguments</span></span>  
 <span data-ttu-id="79156-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="79156-107">`name`, `name2`</span></span>  
 <span data-ttu-id="79156-108">Nom de chaque symbole que vous souhaitez définir.</span><span class="sxs-lookup"><span data-stu-id="79156-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79156-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="79156-109">Remarks</span></span>  
 <span data-ttu-id="79156-110">L’option **-define** revient à utiliser une directive de préprocesseur [#define](../preprocessor-directives/preprocessor-define.md), sauf que l’option de compilateur est appliquée à tous les fichiers du projet.</span><span class="sxs-lookup"><span data-stu-id="79156-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="79156-111">Un symbole reste défini dans un fichier source jusqu’à ce qu’une directive [#undef](../preprocessor-directives/preprocessor-undef.md) dans le fichier source en supprime la définition.</span><span class="sxs-lookup"><span data-stu-id="79156-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="79156-112">Quand vous utilisez l’option -define, une directive `#undef` dans un fichier n’a aucun effet sur les autres fichiers de code source du projet.</span><span class="sxs-lookup"><span data-stu-id="79156-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="79156-113">Vous pouvez utiliser les symboles créés par cette option avec [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md) et [#endif](../preprocessor-directives/preprocessor-endif.md) pour effectuer une compilation conditionnelle des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="79156-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="79156-114">**-d** est la forme abrégée de **-define**.</span><span class="sxs-lookup"><span data-stu-id="79156-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="79156-115">Pour définir plusieurs symboles avec **-define**, séparez chaque nom de symbole par un point-virgule ou une virgule.</span><span class="sxs-lookup"><span data-stu-id="79156-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="79156-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="79156-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="79156-117">Le compilateur C# lui-même ne définit aucun symbole ni aucune macro que vous pouvez utiliser dans votre code source ; toutes les définitions de symbole doivent être définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="79156-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79156-118">La directive C# `#define` ne permet de donner une valeur à un symbole, comme dans les langages tels que C++.</span><span class="sxs-lookup"><span data-stu-id="79156-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="79156-119">Par exemple, l’option `#define` ne peut pas être utilisée pour créer une macro ni définir une constante.</span><span class="sxs-lookup"><span data-stu-id="79156-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="79156-120">Si vous devez définir une constante, utilisez une variable `enum`.</span><span class="sxs-lookup"><span data-stu-id="79156-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="79156-121">Si vous souhaitez créer une macro de style C++, envisagez l’alternative que constituent les génériques.</span><span class="sxs-lookup"><span data-stu-id="79156-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="79156-122">Comme les macros sont notoirement sujettes aux erreurs, C# n’autorise pas leur utilisation, mais fournit des solutions plus sûres.</span><span class="sxs-lookup"><span data-stu-id="79156-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="79156-123">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79156-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="79156-124">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="79156-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="79156-125">Dans l’onglet **Générer**, tapez le symbole à définir dans la zone **Symboles de compilation conditionnelle**.</span><span class="sxs-lookup"><span data-stu-id="79156-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="79156-126">Par exemple, si vous utilisez l’exemple de code qui suit, tapez simplement `xx` dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="79156-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="79156-127">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="79156-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79156-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="79156-128">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="79156-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79156-129">See also</span></span>

- [<span data-ttu-id="79156-130">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="79156-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="79156-131">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="79156-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
