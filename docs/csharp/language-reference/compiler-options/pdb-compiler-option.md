---
description: -pdb (Options du compilateur C#)
title: -pdb (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: ced1ee1f4f079830a032a628da96a389ba27da90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193853"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="b9013-103">-pdb (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="b9013-103">-pdb (C# Compiler Options)</span></span>

<span data-ttu-id="b9013-104">L’option de compilateur **-pdb** spécifie le nom et l’emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="b9013-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9013-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9013-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="b9013-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b9013-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="b9013-107">Nom et emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="b9013-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9013-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b9013-108">Remarks</span></span>  

 <span data-ttu-id="b9013-109">Quand vous spécifiez [-debug (Options du compilateur C#)](./debug-compiler-option.md), le compilateur crée un fichier .pdb dans le même répertoire que celui dans lequel le compilateur va créer le fichier de sortie (.exe ou .dll) avec un nom de fichier identique à celui du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="b9013-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="b9013-110">**-pdb** vous permet de spécifier un nom de fichier autre que celui par défaut et un emplacement pour le fichier .pdb.</span><span class="sxs-lookup"><span data-stu-id="b9013-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="b9013-111">Cette option du compilateur ne peut pas être définie dans l’environnement de développement Visual Studio, ni être modifiée par programmation.</span><span class="sxs-lookup"><span data-stu-id="b9013-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9013-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9013-112">Example</span></span>  

 <span data-ttu-id="b9013-113">Compilez `t.cs` et créez un fichier .pdb sous le nom tt.pdb :</span><span class="sxs-lookup"><span data-stu-id="b9013-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9013-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9013-114">See also</span></span>

- [<span data-ttu-id="b9013-115">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="b9013-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b9013-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="b9013-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
