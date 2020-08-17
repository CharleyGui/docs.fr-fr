---
title: Considérations relatives à la version et la mise à jour pour les développeurs C#
description: L’introduction de nouvelles fonctionnalités de langage dans votre bibliothèque peut affecter le code qui l’utilise.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: f7db7c79792d04bcf592bc1858e1f0f05cb34402
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268125"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="bf3ed-103">Considérations relatives à la version et la mise à jour pour les développeurs C#</span><span class="sxs-lookup"><span data-stu-id="bf3ed-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="bf3ed-104">La compatibilité est un objectif très important alors que des nouvelles fonctionnalités sont ajoutées au langage C#.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="bf3ed-105">Dans presque tous les cas, le code existant peut être recompilé avec une nouvelle version du compilateur sans problème.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="bf3ed-106">Vous devrez peut-être faire plus attention lorsque vous adoptez de nouvelles fonctionnalités de langage dans une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="bf3ed-107">Vous créez peut-être une nouvelle bibliothèque avec des fonctionnalités incluses dans la version la plus récente et avez besoin de vous assurer que les applications créées à l’aide de versions précédentes du compilateur peuvent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="bf3ed-108">Ou vous mettez peut-être à niveau une bibliothèque existante et la plupart de vos utilisateurs ne disposent pas encore des versions mises à niveau.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="bf3ed-109">Lorsque vous prenez des décisions sur l’adoption de nouvelles fonctionnalités, vous devez prendre en compte deux variantes de la compatibilité : compatibilité avec la source et compatibilité binaire.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="bf3ed-110">Modifications compatibles binaires</span><span class="sxs-lookup"><span data-stu-id="bf3ed-110">Binary compatible changes</span></span>

<span data-ttu-id="bf3ed-111">Les modifications apportées à votre bibliothèque sont **compatibles binaires** lorsque votre bibliothèque mise à jour peut être utilisée sans régénération des applications et des bibliothèques qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="bf3ed-112">Les assemblys dépendants n’ont pas besoin d’être reconstruits et aucune modification du code source n’est requise.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="bf3ed-113">Les modifications compatibles binaires sont également des modifications compatibles avec la source.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="bf3ed-114">Modifications compatibles avec la source</span><span class="sxs-lookup"><span data-stu-id="bf3ed-114">Source compatible changes</span></span>

<span data-ttu-id="bf3ed-115">Les modifications apportées à votre bibliothèque sont **compatibles avec la source** lorsque les applications et les bibliothèques qui utilisent votre bibliothèque ne nécessitent pas de modifications du code source, mais que la source doit être recompilée avec la nouvelle version pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="bf3ed-116">Modifications incompatibles</span><span class="sxs-lookup"><span data-stu-id="bf3ed-116">Incompatible changes</span></span>

<span data-ttu-id="bf3ed-117">Si une modification n’est ni **compatible avec la source** ni **compatible binaire**, des modifications du code source, ainsi qu’une recompilation sont requises dans les applications et les bibliothèques dépendantes.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="bf3ed-118">Évaluer votre bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bf3ed-118">Evaluate your library</span></span>

<span data-ttu-id="bf3ed-119">Ces concepts de compatibilité affectent les déclarations publiques et protégées de votre bibliothèque, pas son implémentation interne.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="bf3ed-120">L’adoption de nouvelles fonctionnalités en interne est toujours **compatible binaire**.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="bf3ed-121">Les modifications **compatibles binaires** fournissent une nouvelle syntaxe qui génère le même code compilé pour les déclarations publiques que l’ancienne syntaxe.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="bf3ed-122">Par exemple, la modification d’une méthode en un membre expression-bodied est une modification **compatible binaire** :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="bf3ed-123">Code d'origine :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="bf3ed-124">Nouveau code :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="bf3ed-125">Les modifications **compatibles avec la source** introduisent une syntaxe qui modifie le code compilé pour un membre public, mais de manière compatible avec les sites d’appel existants.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="bf3ed-126">Par exemple, la modification d’une signature de méthode à partir d’un paramètre de valeur by en un paramètre de référence by `in` est compatible avec la source mais pas compatible binaire :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="bf3ed-127">Code d'origine :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="bf3ed-128">Nouveau code :</span><span class="sxs-lookup"><span data-stu-id="bf3ed-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="bf3ed-129">Les articles [Nouveautés](index.md) indiquent si l’introduction d’une fonctionnalité qui affecte les déclarations publiques est compatible avec la source ou compatible binaire.</span><span class="sxs-lookup"><span data-stu-id="bf3ed-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
