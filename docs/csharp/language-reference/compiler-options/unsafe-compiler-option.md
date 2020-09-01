---
description: -unsafe (Options du compilateur C#)
title: -unsafe (Options du compilateur C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140839"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="35c17-103">-unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="35c17-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="35c17-104">L’option de compilateur **-unsafe** permet la compilation de code utilisant le mot clé [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="35c17-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35c17-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="35c17-106">Notes</span><span class="sxs-lookup"><span data-stu-id="35c17-106">Remarks</span></span>

<span data-ttu-id="35c17-107">Pour plus d’informations sur le code unsafe, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="35c17-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="35c17-108">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35c17-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="35c17-109">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="35c17-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="35c17-110">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="35c17-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="35c17-111">Cochez la case **Autoriser le code unsafe**.</span><span class="sxs-lookup"><span data-stu-id="35c17-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="35c17-112">Pour ajouter cette option dans un fichier csproj</span><span class="sxs-lookup"><span data-stu-id="35c17-112">To add this option in a csproj file</span></span>

<span data-ttu-id="35c17-113">Ouvrez le fichier .csproj d’un projet et ajoutez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="35c17-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="35c17-114">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="35c17-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35c17-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="35c17-115">Example</span></span>

<span data-ttu-id="35c17-116">Compilez `in.cs` selon le mode non sécurisé :</span><span class="sxs-lookup"><span data-stu-id="35c17-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="35c17-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35c17-117">See also</span></span>

- [<span data-ttu-id="35c17-118">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="35c17-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="35c17-119">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="35c17-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
