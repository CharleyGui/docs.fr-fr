---
description: -warn (Options du compilateur C#)
title: -warn (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d59274423e6f9844d3ab22f3ac513ba1a05d7f07
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171349"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="8912e-103">-warn (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="8912e-103">-warn (C# Compiler Options)</span></span>

<span data-ttu-id="8912e-104">L’option **-warn** spécifie le niveau d’avertissement que le compilateur doit afficher.</span><span class="sxs-lookup"><span data-stu-id="8912e-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8912e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8912e-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="8912e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="8912e-106">Arguments</span></span>  

 `option`  
 <span data-ttu-id="8912e-107">Niveau d’avertissement que vous souhaitez afficher pour la compilation : les nombres inférieurs affichent uniquement les avertissements ayant un niveau de gravité élevé ; les nombres supérieurs affichent davantage d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="8912e-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="8912e-108">La valeur doit être zéro ou un entier positif :</span><span class="sxs-lookup"><span data-stu-id="8912e-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="8912e-109">Niveau d’avertissement</span><span class="sxs-lookup"><span data-stu-id="8912e-109">Warning level</span></span>|<span data-ttu-id="8912e-110">Signification</span><span class="sxs-lookup"><span data-stu-id="8912e-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="8912e-111">0</span><span class="sxs-lookup"><span data-stu-id="8912e-111">0</span></span>|<span data-ttu-id="8912e-112">Désactive l’émission de tous les messages d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="8912e-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="8912e-113">1</span><span class="sxs-lookup"><span data-stu-id="8912e-113">1</span></span>|<span data-ttu-id="8912e-114">Affiche les messages d’avertissement graves.</span><span class="sxs-lookup"><span data-stu-id="8912e-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="8912e-115">2</span><span class="sxs-lookup"><span data-stu-id="8912e-115">2</span></span>|<span data-ttu-id="8912e-116">Affiche les avertissements de niveau 1, ainsi que certains avertissements moins graves, tels que les avertissements concernant le masquage de membres de classe.</span><span class="sxs-lookup"><span data-stu-id="8912e-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="8912e-117">3</span><span class="sxs-lookup"><span data-stu-id="8912e-117">3</span></span>|<span data-ttu-id="8912e-118">Affiche les avertissements de niveau 2, ainsi que certains avertissements moins graves, tels que les avertissements concernant les expressions toujours évaluées à `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="8912e-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="8912e-119">4 (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="8912e-119">4 (the default)</span></span>|<span data-ttu-id="8912e-120">Affiche les avertissements de niveau 3, ainsi que les avertissements d’information.</span><span class="sxs-lookup"><span data-stu-id="8912e-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="8912e-121">5</span><span class="sxs-lookup"><span data-stu-id="8912e-121">5</span></span>|<span data-ttu-id="8912e-122">Affiche les avertissements de niveau 4 et des [avertissements supplémentaires](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) du compilateur fournis avec C# 9,0.</span><span class="sxs-lookup"><span data-stu-id="8912e-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="8912e-123">Supérieur à 5</span><span class="sxs-lookup"><span data-stu-id="8912e-123">Greater than 5</span></span>|<span data-ttu-id="8912e-124">Toute valeur supérieure à 5 sera traitée comme 5.</span><span class="sxs-lookup"><span data-stu-id="8912e-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="8912e-125">En général, vous placez une valeur élevée arbitraire (par exemple, `9999` ) pour vous assurer que vous avez toujours tous les avertissements si le compilateur est mis à jour avec de nouveaux niveaux d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="8912e-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="8912e-126">Notes</span><span class="sxs-lookup"><span data-stu-id="8912e-126">Remarks</span></span>  

 <span data-ttu-id="8912e-127">Pour obtenir des informations sur une erreur ou un avertissement, vous pouvez rechercher le code d’erreur dans l’index de l’aide.</span><span class="sxs-lookup"><span data-stu-id="8912e-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="8912e-128">Il existe d’autres façons d’obtenir des informations sur une erreur ou un avertissement, qui sont décrites dans [Erreurs du compilateur C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="8912e-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="8912e-129">Utilisez [-warnaserror](./warnaserror-compiler-option.md) pour traiter tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8912e-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="8912e-130">Utilisez [-nowarn](./nowarn-compiler-option.md) pour désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="8912e-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="8912e-131">**-w** est la forme abrégée de **-warn**.</span><span class="sxs-lookup"><span data-stu-id="8912e-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8912e-132">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8912e-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="8912e-133">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="8912e-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="8912e-134">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8912e-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="8912e-135">Modifiez la propriété **Niveau d’avertissement**.</span><span class="sxs-lookup"><span data-stu-id="8912e-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="8912e-136">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="8912e-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8912e-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="8912e-137">Example</span></span>  

 <span data-ttu-id="8912e-138">Compilez `in.cs` et faites en sorte que le compilateur n’affiche que les avertissements de niveau 1 :</span><span class="sxs-lookup"><span data-stu-id="8912e-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8912e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8912e-139">See also</span></span>

- [<span data-ttu-id="8912e-140">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="8912e-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8912e-141">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="8912e-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
