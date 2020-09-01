---
description: -subsystemversion (Options du compilateur C#)
title: -subsystemversion (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: e8001d8db214123e75fec4e1d1117ef90a9df606
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128593"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="a2c97-103">-subsystemversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="a2c97-103">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="a2c97-104">Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, déterminant ainsi les versions de Windows sur lesquelles le fichier exécutable peut s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="a2c97-104">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="a2c97-105">En règle générale, cette option garantit que le fichier exécutable peut tirer parti de fonctionnalités de sécurité particulières qui ne sont pas disponibles avec des versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="a2c97-105">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="a2c97-106">Pour spécifier le sous-système lui-même, utilisez l’option du compilateur [-target](./target-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a2c97-106">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2c97-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c97-107">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="a2c97-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2c97-108">Parameters</span></span>

`major.minor`

<span data-ttu-id="a2c97-109">Version minimale requise du sous-système, telle qu’elle est exprimée dans une notation par points pour les versions majeure et mineure.</span><span class="sxs-lookup"><span data-stu-id="a2c97-109">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="a2c97-110">Par exemple, vous pouvez spécifier qu’une application ne peut pas s’exécuter sur un système d’exploitation antérieur à Windows 7 si vous définissez la valeur de cette option sur 6.01, comme décrit dans le tableau plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a2c97-110">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="a2c97-111">Vous devez spécifier les valeurs de `major` et `minor` en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="a2c97-111">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="a2c97-112">Les zéros à gauche du numéro de version `minor` ne modifient pas la version, contrairement aux zéros de droite.</span><span class="sxs-lookup"><span data-stu-id="a2c97-112">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="a2c97-113">Par exemple, 6.1 et 6.01 font référence à la même version, mais 6.10 fait référence à une version différente.</span><span class="sxs-lookup"><span data-stu-id="a2c97-113">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="a2c97-114">Nous vous recommandons d’exprimer la version mineure avec deux chiffres pour éviter toute confusion.</span><span class="sxs-lookup"><span data-stu-id="a2c97-114">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2c97-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="a2c97-115">Remarks</span></span>

<span data-ttu-id="a2c97-116">Le tableau suivant répertorie les versions courantes de sous-système de Windows.</span><span class="sxs-lookup"><span data-stu-id="a2c97-116">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="a2c97-117">Version de Windows</span><span class="sxs-lookup"><span data-stu-id="a2c97-117">Windows version</span></span>|<span data-ttu-id="a2c97-118">Version de sous-système</span><span class="sxs-lookup"><span data-stu-id="a2c97-118">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="a2c97-119">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="a2c97-119">Windows 2000</span></span>|<span data-ttu-id="a2c97-120">5,00</span><span class="sxs-lookup"><span data-stu-id="a2c97-120">5.00</span></span>|
|<span data-ttu-id="a2c97-121">Windows XP</span><span class="sxs-lookup"><span data-stu-id="a2c97-121">Windows XP</span></span>|<span data-ttu-id="a2c97-122">5,01</span><span class="sxs-lookup"><span data-stu-id="a2c97-122">5.01</span></span>|
|<span data-ttu-id="a2c97-123">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="a2c97-123">Windows Server 2003</span></span>|<span data-ttu-id="a2c97-124">5.02</span><span class="sxs-lookup"><span data-stu-id="a2c97-124">5.02</span></span>|
|<span data-ttu-id="a2c97-125">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="a2c97-125">Windows Vista</span></span>|<span data-ttu-id="a2c97-126">6,00</span><span class="sxs-lookup"><span data-stu-id="a2c97-126">6.00</span></span>|
|<span data-ttu-id="a2c97-127">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a2c97-127">Windows 7</span></span>|<span data-ttu-id="a2c97-128">6.01</span><span class="sxs-lookup"><span data-stu-id="a2c97-128">6.01</span></span>|
|<span data-ttu-id="a2c97-129">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a2c97-129">Windows Server 2008</span></span>|<span data-ttu-id="a2c97-130">6.01</span><span class="sxs-lookup"><span data-stu-id="a2c97-130">6.01</span></span>|
|<span data-ttu-id="a2c97-131">Windows 8</span><span class="sxs-lookup"><span data-stu-id="a2c97-131">Windows 8</span></span>|<span data-ttu-id="a2c97-132">6.02</span><span class="sxs-lookup"><span data-stu-id="a2c97-132">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="a2c97-133">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a2c97-133">Default values</span></span>

<span data-ttu-id="a2c97-134">La valeur par défaut de l’option du compilateur **-subsystemversion** dépend des conditions répertoriées dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="a2c97-134">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="a2c97-135">La valeur par défaut est 6.02 si l’une quelconque des options du compilateur de la liste suivante est définie :</span><span class="sxs-lookup"><span data-stu-id="a2c97-135">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="a2c97-136">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="a2c97-136">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="a2c97-137">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="a2c97-137">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="a2c97-138">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="a2c97-138">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="a2c97-139">La valeur par défaut est 6.00 si vous utilisez MSBuild, si vous ciblez .NET Framework 4.5 et si vous n’avez défini aucune des options du compilateur spécifiées plus haut dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="a2c97-139">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="a2c97-140">La valeur par défaut est 4.00 si aucune des conditions précédentes n’est vraie.</span><span class="sxs-lookup"><span data-stu-id="a2c97-140">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="a2c97-141">Définition de cette option</span><span class="sxs-lookup"><span data-stu-id="a2c97-141">Setting this option</span></span>

<span data-ttu-id="a2c97-142">Pour définir l’option du compilateur **-subsystemversion** dans Visual Studio, vous devez ouvrir le fichier .csproj et spécifier une valeur pour la propriété `SubsystemVersion` dans le code XML MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a2c97-142">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="a2c97-143">Vous ne pouvez pas définir cette option dans l’environnement IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2c97-143">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="a2c97-144">Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [Propriétés communes des projets MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="a2c97-144">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2c97-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c97-145">See also</span></span>

- [<span data-ttu-id="a2c97-146">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="a2c97-146">C# Compiler Options</span></span>](./index.md)
