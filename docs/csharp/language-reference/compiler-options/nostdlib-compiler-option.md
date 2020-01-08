---
title: -nostdlib (Options du compilateur C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345077"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="cee7c-102">-nostdlib (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="cee7c-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="cee7c-103">**-nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.</span><span class="sxs-lookup"><span data-stu-id="cee7c-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="cee7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cee7c-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="cee7c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="cee7c-105">Remarks</span></span>

<span data-ttu-id="cee7c-106">Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.</span><span class="sxs-lookup"><span data-stu-id="cee7c-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="cee7c-107">Si vous ne spécifiez pas **-nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="cee7c-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="cee7c-108">Les options **-nostdlib** et **-nostdlib+** sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="cee7c-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="cee7c-109">Pour définir cette option de compilateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cee7c-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="cee7c-110">Les instructions suivantes s’appliquent uniquement à Visual Studio 2015 (et versions antérieures).</span><span class="sxs-lookup"><span data-stu-id="cee7c-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="cee7c-111">La propriété de build **mscorlib. dll n’existe pas** dans les versions plus récentes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cee7c-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="cee7c-112">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="cee7c-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="cee7c-113">Cliquez sur la page de propriétés **Générer** .</span><span class="sxs-lookup"><span data-stu-id="cee7c-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="cee7c-114">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="cee7c-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="cee7c-115">Modifiez la propriété **Ne pas référencer mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="cee7c-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="cee7c-116">Pour définir cette option du compilateur par programmation</span><span class="sxs-lookup"><span data-stu-id="cee7c-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="cee7c-117">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="cee7c-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="cee7c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cee7c-118">See also</span></span>

- [<span data-ttu-id="cee7c-119">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="cee7c-119">C# Compiler Options</span></span>](./index.md)
