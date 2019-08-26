---
title: -nostdlib (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602689"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="b95e0-102">-nostdlib (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="b95e0-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="b95e0-103">**-nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.</span><span class="sxs-lookup"><span data-stu-id="b95e0-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="b95e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b95e0-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="b95e0-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="b95e0-105">Remarks</span></span>

<span data-ttu-id="b95e0-106">Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.</span><span class="sxs-lookup"><span data-stu-id="b95e0-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="b95e0-107">Si vous ne spécifiez pas **-nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="b95e0-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="b95e0-108">Les options **-nostdlib** et **-nostdlib+** sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="b95e0-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="b95e0-109">Pour définir cette option de compilateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b95e0-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="b95e0-110">Les instructions suivantes s’appliquent uniquement à Visual Studio 2015 (et versions antérieures).</span><span class="sxs-lookup"><span data-stu-id="b95e0-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="b95e0-111">La propriété de build **Ne pas référencer mscorlib.dll** n’existe pas dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b95e0-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="b95e0-112">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="b95e0-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="b95e0-113">Cliquez sur la page de propriétés **Générer** .</span><span class="sxs-lookup"><span data-stu-id="b95e0-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="b95e0-114">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="b95e0-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="b95e0-115">Modifiez la propriété **Ne pas référencer mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="b95e0-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="b95e0-116">Pour définir cette option du compilateur par programmation</span><span class="sxs-lookup"><span data-stu-id="b95e0-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="b95e0-117">Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="b95e0-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b95e0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b95e0-118">See also</span></span>

- [<span data-ttu-id="b95e0-119">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="b95e0-119">C# Compiler Options</span></span>](./index.md)
