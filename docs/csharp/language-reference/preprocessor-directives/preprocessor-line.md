---
description: '#line - Référence C#'
title: '#line - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: e2a5ecb6c29184123b8a88ae1b12caf24ec7296a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137992"
---
# <a name="line-c-reference"></a><span data-ttu-id="af9b0-103">#line (référence C#)</span><span class="sxs-lookup"><span data-stu-id="af9b0-103">#line (C# Reference)</span></span>

<span data-ttu-id="af9b0-104">`#line` vous permet de changer la numérotation de lignes du compilateur et (éventuellement) le nom de fichier pour les erreurs et les avertissements.</span><span class="sxs-lookup"><span data-stu-id="af9b0-104">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="af9b0-105">L’exemple suivant montre comment signaler deux avertissements associés à des numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="af9b0-105">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="af9b0-106">La directive `#line 200` assigne de force le numéro 200 à la ligne suivante (bien que le numéro par défaut soit 6) ; jusqu’à la prochaine directive `#line`, le nom de fichier indiqué est « Special ».</span><span class="sxs-lookup"><span data-stu-id="af9b0-106">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="af9b0-107">La directive `#line default` rétablit la numérotation de lignes par défaut, qui compte les lignes renumérotées par la directive précédente.</span><span class="sxs-lookup"><span data-stu-id="af9b0-107">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="af9b0-108">La compilation produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="af9b0-108">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="af9b0-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="af9b0-109">Remarks</span></span>

<span data-ttu-id="af9b0-110">La directive `#line` peut être utilisée dans une étape intermédiaire automatisée du processus de génération.</span><span class="sxs-lookup"><span data-stu-id="af9b0-110">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="af9b0-111">Par exemple, si des lignes ont été supprimées du fichier de code source d’origine, mais que vous voulez que le compilateur continue de générer une sortie sur la base de la numérotation de lignes d’origine du fichier, vous pouvez supprimer les lignes et simuler ensuite la numérotation de lignes d’origine avec `#line`.</span><span class="sxs-lookup"><span data-stu-id="af9b0-111">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="af9b0-112">La directive `#line hidden` masque les lignes successives du débogueur, de sorte que quand le développeur parcourt le code, les lignes situées entre une directive `#line hidden` et la directive `#line` suivante (en supposant qu’il ne s’agit pas d’une autre directive `#line hidden`) sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="af9b0-112">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="af9b0-113">Cette option peut aussi être utilisée pour permettre à ASP.NET de différencier le code défini par l’utilisateur du code généré par l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af9b0-113">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="af9b0-114">Même si ASP.NET est le principal utilisateur de cette fonctionnalité, il est probable que d’autres générateurs de code source pourront l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="af9b0-114">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="af9b0-115">Une directive `#line hidden` n’affecte ni les noms de fichiers ni les numéros de lignes dans les rapports d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="af9b0-115">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="af9b0-116">Autrement dit, si une erreur se produit dans un bloc masqué, le compilateur indique le nom du fichier et le numéro de ligne actuels de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="af9b0-116">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="af9b0-117">La directive `#line filename` spécifie le nom de fichier que vous souhaitez voir apparaître dans la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="af9b0-117">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="af9b0-118">Par défaut, le nom réel du fichier de code source est utilisé.</span><span class="sxs-lookup"><span data-stu-id="af9b0-118">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="af9b0-119">Le nom de fichier doit être entre guillemets doubles (" ") et doit être précédé d’un numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="af9b0-119">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="af9b0-120">Un fichier de code source peut contenir un nombre illimité de directives `#line`.</span><span class="sxs-lookup"><span data-stu-id="af9b0-120">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="af9b0-121">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="af9b0-121">Example 1</span></span>

<span data-ttu-id="af9b0-122">L’exemple suivant montre comment le débogueur ignore les lignes masquées dans le code.</span><span class="sxs-lookup"><span data-stu-id="af9b0-122">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="af9b0-123">Quand vous exécutez l’exemple, celui-ci affiche trois lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="af9b0-123">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="af9b0-124">Or, quand vous définissez un point d’arrêt, comme dans l’exemple, et que vous appuyez sur F10 pour parcourir le code, vous pouvez remarquer que le débogueur ignore la ligne masquée.</span><span class="sxs-lookup"><span data-stu-id="af9b0-124">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="af9b0-125">Vous remarquerez aussi que même si vous définissez un point d’arrêt au niveau de la ligne masquée, le débogueur continuera de l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="af9b0-125">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="af9b0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af9b0-126">See also</span></span>

- [<span data-ttu-id="af9b0-127">Référence C#</span><span class="sxs-lookup"><span data-stu-id="af9b0-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="af9b0-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="af9b0-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="af9b0-129">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="af9b0-129">C# Preprocessor Directives</span></span>](./index.md)
