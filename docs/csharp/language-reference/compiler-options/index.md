---
description: Options du compilateur C#
title: Options du compilateur C#
ms.date: 08/28/2020
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: 502bd83ae52be9ae2f914847bb6bf7c7f2a0c411
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271813"
---
# <a name="c-compiler-options"></a><span data-ttu-id="53f04-103">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="53f04-103">C# Compiler Options</span></span>

<span data-ttu-id="53f04-104">Le compilateur produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="53f04-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="53f04-105">Chaque option du compilateur est disponible sous deux formes : **-option** et **/option**.</span><span class="sxs-lookup"><span data-stu-id="53f04-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="53f04-106">La documentation présente uniquement la forme **-option**.</span><span class="sxs-lookup"><span data-stu-id="53f04-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="53f04-107">Dans Visual Studio, vous définissez les options du compilateur dans le fichier *web.config* .</span><span class="sxs-lookup"><span data-stu-id="53f04-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="53f04-108">Pour plus d’informations, consultez [ \<compiler> élément](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="53f04-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="53f04-109">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="53f04-109">In this section</span></span>

- <span data-ttu-id="53f04-110">[Génération à partir de la ligne de commande avec csc.exe](command-line-building-with-csc-exe.md) Informations sur la création d’une application Visual C# à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53f04-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="53f04-111">[Comment définir des variables d’environnement pour la ligne de commande Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Fournit la procédure d’exécution de *VsDevCmd.bat* pour activer des générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53f04-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *VsDevCmd.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="53f04-112">[Options du compilateur C# classées par catégorie](listed-by-category.md) Liste catégorique des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="53f04-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="53f04-113">[Options du compilateur C# par ordre alphabétique](listed-alphabetically.md) Liste alphabétique des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="53f04-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="53f04-114">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="53f04-114">Related sections</span></span>

- <span data-ttu-id="53f04-115">[Générer, page du concepteur de projets](/visualstudio/ide/reference/build-page-project-designer-csharp) Définition des propriétés qui régissent la compilation, la génération et le débogage de votre projet.</span><span class="sxs-lookup"><span data-stu-id="53f04-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="53f04-116">Contient des informations sur les étapes de génération personnalisée dans les projets Visual C#.</span><span class="sxs-lookup"><span data-stu-id="53f04-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="53f04-117">[Builds par défaut et personnalisées](/visualstudio/ide/compiling-and-building-in-visual-studio) Informations sur les types de build et les configurations.</span><span class="sxs-lookup"><span data-stu-id="53f04-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="53f04-118">[Préparation et gestion des builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procédures de génération dans l’environnement de développement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53f04-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
