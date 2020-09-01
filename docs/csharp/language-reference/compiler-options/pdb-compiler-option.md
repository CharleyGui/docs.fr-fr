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
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124914"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="f1793-103">-pdb (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f1793-103">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="f1793-104">L’option de compilateur **-pdb** spécifie le nom et l’emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="f1793-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1793-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1793-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1793-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1793-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f1793-107">Nom et emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="f1793-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1793-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f1793-108">Remarks</span></span>  
 <span data-ttu-id="f1793-109">Quand vous spécifiez [-debug (Options du compilateur C#)](./debug-compiler-option.md), le compilateur crée un fichier .pdb dans le même répertoire que celui dans lequel le compilateur va créer le fichier de sortie (.exe ou .dll) avec un nom de fichier identique à celui du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1793-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="f1793-110">**-pdb** vous permet de spécifier un nom de fichier autre que celui par défaut et un emplacement pour le fichier .pdb.</span><span class="sxs-lookup"><span data-stu-id="f1793-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="f1793-111">Cette option du compilateur ne peut pas être définie dans l’environnement de développement Visual Studio, ni être modifiée par programmation.</span><span class="sxs-lookup"><span data-stu-id="f1793-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1793-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f1793-112">Example</span></span>  
 <span data-ttu-id="f1793-113">Compilez `t.cs` et créez un fichier .pdb sous le nom tt.pdb :</span><span class="sxs-lookup"><span data-stu-id="f1793-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1793-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1793-114">See also</span></span>

- [<span data-ttu-id="f1793-115">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="f1793-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f1793-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f1793-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
