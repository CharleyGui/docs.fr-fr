---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e42501a002d808f31dc3d599dc030e96c573a22f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380322"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="17f2a-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17f2a-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="17f2a-103">Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, déterminant ainsi les versions de Windows sur lesquelles le fichier exécutable peut s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="17f2a-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="17f2a-104">En règle générale, cette option garantit que le fichier exécutable peut tirer parti de fonctionnalités de sécurité particulières qui ne sont pas disponibles avec des versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="17f2a-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="17f2a-105">Pour spécifier le sous-système lui-même, utilisez l’option du compilateur [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="17f2a-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="17f2a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17f2a-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="17f2a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17f2a-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="17f2a-108">Version minimale requise du sous-système, telle qu’elle est exprimée dans une notation par points pour les versions majeure et mineure.</span><span class="sxs-lookup"><span data-stu-id="17f2a-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="17f2a-109">Par exemple, vous pouvez spécifier qu’une application ne peut pas s’exécuter sur un système d’exploitation antérieur à Windows 7 si vous définissez la valeur de cette option sur 6.01, comme décrit dans le tableau plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="17f2a-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="17f2a-110">Vous devez spécifier les valeurs de `major` et `minor` en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="17f2a-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="17f2a-111">Les zéros à gauche du numéro de version `minor` ne modifient pas la version, contrairement aux zéros de droite.</span><span class="sxs-lookup"><span data-stu-id="17f2a-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="17f2a-112">Par exemple, 6.1 et 6.01 font référence à la même version, mais 6.10 fait référence à une version différente.</span><span class="sxs-lookup"><span data-stu-id="17f2a-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="17f2a-113">Nous vous recommandons d’exprimer la version mineure avec deux chiffres pour éviter toute confusion.</span><span class="sxs-lookup"><span data-stu-id="17f2a-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="17f2a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="17f2a-114">Remarks</span></span>

<span data-ttu-id="17f2a-115">Le tableau suivant répertorie les versions courantes de sous-système de Windows.</span><span class="sxs-lookup"><span data-stu-id="17f2a-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="17f2a-116">Version Windows</span><span class="sxs-lookup"><span data-stu-id="17f2a-116">Windows version</span></span>|<span data-ttu-id="17f2a-117">Version de sous-système</span><span class="sxs-lookup"><span data-stu-id="17f2a-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="17f2a-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="17f2a-118">Windows 2000</span></span>|<span data-ttu-id="17f2a-119">5.00</span><span class="sxs-lookup"><span data-stu-id="17f2a-119">5.00</span></span>|
|<span data-ttu-id="17f2a-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="17f2a-120">Windows XP</span></span>|<span data-ttu-id="17f2a-121">5.01</span><span class="sxs-lookup"><span data-stu-id="17f2a-121">5.01</span></span>|
|<span data-ttu-id="17f2a-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="17f2a-122">Windows Server 2003</span></span>|<span data-ttu-id="17f2a-123">5.02</span><span class="sxs-lookup"><span data-stu-id="17f2a-123">5.02</span></span>|
|<span data-ttu-id="17f2a-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="17f2a-124">Windows Vista</span></span>|<span data-ttu-id="17f2a-125">6.00</span><span class="sxs-lookup"><span data-stu-id="17f2a-125">6.00</span></span>|
|<span data-ttu-id="17f2a-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="17f2a-126">Windows 7</span></span>|<span data-ttu-id="17f2a-127">6.01</span><span class="sxs-lookup"><span data-stu-id="17f2a-127">6.01</span></span>|
|<span data-ttu-id="17f2a-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="17f2a-128">Windows Server 2008</span></span>|<span data-ttu-id="17f2a-129">6.01</span><span class="sxs-lookup"><span data-stu-id="17f2a-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="17f2a-130">6.02</span><span class="sxs-lookup"><span data-stu-id="17f2a-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="17f2a-131">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="17f2a-131">Default values</span></span>

<span data-ttu-id="17f2a-132">La valeur par défaut de l’option du compilateur **-subsystemversion** dépend des conditions répertoriées dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="17f2a-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="17f2a-133">La valeur par défaut est 6.02 si l’une quelconque des options du compilateur de la liste suivante est définie :</span><span class="sxs-lookup"><span data-stu-id="17f2a-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="17f2a-134">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="17f2a-134">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="17f2a-135">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="17f2a-135">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="17f2a-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="17f2a-136">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)

- <span data-ttu-id="17f2a-137">La valeur par défaut est 6.00 si vous utilisez MSBuild, vous ciblez .NET Framework 4.5, et vous n’avez défini aucune des options du compilateur spécifiées plus haut dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="17f2a-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="17f2a-138">La valeur par défaut est 4.00 si aucune des conditions précédentes n’est vraie.</span><span class="sxs-lookup"><span data-stu-id="17f2a-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="17f2a-139">Définition de cette option</span><span class="sxs-lookup"><span data-stu-id="17f2a-139">Setting this option</span></span>

<span data-ttu-id="17f2a-140">Pour définir le **- subsystemversion** option du compilateur dans Visual Studio, vous devez ouvrir le fichier .vbproj et spécifiez une valeur pour le `SubsystemVersion` propriété dans le XML de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17f2a-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="17f2a-141">Vous ne pouvez pas définir cette option dans l’environnement IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17f2a-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="17f2a-142">Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [Propriétés communes des projets MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="17f2a-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="17f2a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17f2a-143">See also</span></span>

- [<span data-ttu-id="17f2a-144">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17f2a-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

- [<span data-ttu-id="17f2a-145">Propriétés MSBuild</span><span class="sxs-lookup"><span data-stu-id="17f2a-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
