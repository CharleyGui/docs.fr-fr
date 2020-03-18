---
title: -unsafe (Options du compilateur C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877991"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="0efb0-102">-unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="0efb0-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="0efb0-103">L’option de compilateur **-unsafe** permet la compilation de code utilisant le mot clé [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="0efb0-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0efb0-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="0efb0-105">Notes </span><span class="sxs-lookup"><span data-stu-id="0efb0-105">Remarks</span></span>

<span data-ttu-id="0efb0-106">Pour plus d’informations sur le code unsafe, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="0efb0-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0efb0-107">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0efb0-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0efb0-108">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="0efb0-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="0efb0-109">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="0efb0-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="0efb0-110">Cochez la case **Autoriser le code unsafe**.</span><span class="sxs-lookup"><span data-stu-id="0efb0-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="0efb0-111">Pour ajouter cette option dans un fichier csproj</span><span class="sxs-lookup"><span data-stu-id="0efb0-111">To add this option in a csproj file</span></span>

<span data-ttu-id="0efb0-112">Ouvrez le fichier .csproj d’un projet et ajoutez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0efb0-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="0efb0-113">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="0efb0-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0efb0-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0efb0-114">Example</span></span>

<span data-ttu-id="0efb0-115">Compilez `in.cs` selon le mode non sécurisé :</span><span class="sxs-lookup"><span data-stu-id="0efb0-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0efb0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0efb0-116">See also</span></span>

- [<span data-ttu-id="0efb0-117">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="0efb0-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="0efb0-118">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="0efb0-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
