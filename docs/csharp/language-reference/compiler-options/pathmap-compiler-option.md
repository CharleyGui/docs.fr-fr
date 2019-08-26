---
title: -pathmap (Options du compilateur C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606626"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="e4fb5-102">-pathmap (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e4fb5-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="e4fb5-103">L’option de compilateur **-pathmap** spécifie comment mapper des chemins physiques aux noms de chemin source générés en sortie par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4fb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4fb5-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="e4fb5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e4fb5-105">Arguments</span></span>

 <span data-ttu-id="e4fb5-106">`path1` : chemin complet aux fichiers sources dans l’environnement actuel</span><span class="sxs-lookup"><span data-stu-id="e4fb5-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="e4fb5-107">`sourcePath1` : chemin source remplaçant `path1` dans les fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="e4fb5-108">Pour spécifier plusieurs chemins sources mappés, séparez-les par des virgules.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4fb5-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e4fb5-109">Remarks</span></span>

<span data-ttu-id="e4fb5-110">Le compilateur écrit le chemin source dans sa sortie dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="e4fb5-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="e4fb5-111">Le chemin source est remplacé par un argument quand <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> est appliqué à un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="e4fb5-112">Le chemin source est incorporé dans un fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="e4fb5-113">Le chemin du fichier PDB est incorporé dans un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="e4fb5-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="e4fb5-114">Cette option mappe chaque chemin physique de l’ordinateur sur lequel le compilateur s’exécute à un chemin correspondant qui doit être écrit dans les fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="e4fb5-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="e4fb5-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="e4fb5-115">Example</span></span>

<span data-ttu-id="e4fb5-116">Compilez `t.cs` dans le répertoire **C:\\work\\tests** et mappez ce répertoire à **\publish** dans la sortie :</span><span class="sxs-lookup"><span data-stu-id="e4fb5-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="e4fb5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4fb5-117">See also</span></span>

- [<span data-ttu-id="e4fb5-118">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e4fb5-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e4fb5-119">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="e4fb5-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
