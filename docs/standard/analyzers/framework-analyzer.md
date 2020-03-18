---
title: .NET Analyseurs de cadre - .NET
description: Apprenez à utiliser les analyseurs de cadre .NET dans le paquet .NET Framework Analyzers pour trouver et traiter les risques de sécurité
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155995"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="81068-103">L’analyseur .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81068-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="81068-104">Vous pouvez utiliser l’Analyseur .NET Framework pour rechercher les problèmes potentiels dans votre code d’application basé sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81068-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="81068-105">Cet analyseur recherche les problèmes potentiels et suggère des correctifs pour les résoudre.</span><span class="sxs-lookup"><span data-stu-id="81068-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="81068-106">L’analyseur s’exécute de façon interactive dans Visual Studio au fil de l’écriture du code ou dans le cadre d’une build CI.</span><span class="sxs-lookup"><span data-stu-id="81068-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="81068-107">Il est recommandé d’ajouter l’analyseur à votre projet dès que possible dans votre développement.</span><span class="sxs-lookup"><span data-stu-id="81068-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="81068-108">Plus tôt vous trouvez les problèmes potentiels dans votre code, plus ils sont faciles à corriger.</span><span class="sxs-lookup"><span data-stu-id="81068-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="81068-109">Cependant, vous pouvez l’ajouter à tout moment au cours du cycle de développement.</span><span class="sxs-lookup"><span data-stu-id="81068-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="81068-110">Il détecte les problèmes dans le code existant et signale les problèmes au fil de votre développement.</span><span class="sxs-lookup"><span data-stu-id="81068-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="81068-111">Installation et configuration de l’Analyseur .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81068-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="81068-112">Les analyseurs de cadre .NET doivent être installés comme un paquet NuGet sur chaque projet où vous voulez qu’ils fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="81068-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="81068-113">Il suffit qu’un seul développeur les ajoute au projet.</span><span class="sxs-lookup"><span data-stu-id="81068-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="81068-114">Le package de l’analyseur est une dépendance de projet et il s’exécute sur la machine de chaque développeur une fois qu’il dispose de la solution mise à jour.</span><span class="sxs-lookup"><span data-stu-id="81068-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="81068-115">L’Analyseur .NET Framework est livré dans le package NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/).</span><span class="sxs-lookup"><span data-stu-id="81068-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="81068-116">Ce package fournit seulement les analyseurs spécifiques à .NET Framework, qui comprend des analyseurs de sécurité.</span><span class="sxs-lookup"><span data-stu-id="81068-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="81068-117">Dans la plupart des cas, vous allez utiliser le package NuGet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).</span><span class="sxs-lookup"><span data-stu-id="81068-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span>
<span data-ttu-id="81068-118">Le package d’agrégation FxCopAnalyzers contient tous les analyseurs de framework inclus dans le package Framework.Analyzers, ainsi que les analyseurs suivants :</span><span class="sxs-lookup"><span data-stu-id="81068-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="81068-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers) : fournit des indications générales et des conseils pour les API .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="81068-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="81068-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers) : fournit des analyseurs spécifiques aux API .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81068-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="81068-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers) : fournit des conseils pour le texte inclus en tant que code, notamment les commentaires.</span><span class="sxs-lookup"><span data-stu-id="81068-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="81068-122">Pour l’installer, cliquez avec le bouton droit sur le projet et sélectionnez « Gérer les dépendances ».</span><span class="sxs-lookup"><span data-stu-id="81068-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="81068-123">Dans l’Explorateur NuGet, recherchez « NetFramework Analyzer » ou, si vous préférez, « Fx Cop Analyzerx ».</span><span class="sxs-lookup"><span data-stu-id="81068-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="81068-124">Installez la dernière version stable dans tous les projets de votre solution.</span><span class="sxs-lookup"><span data-stu-id="81068-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="81068-125">Utilisation de l’Analyseur .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81068-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="81068-126">Une fois le package NuGet installé, générez votre solution.</span><span class="sxs-lookup"><span data-stu-id="81068-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="81068-127">L’analyseur signale les éventuels problèmes qu’il trouve dans votre code base.</span><span class="sxs-lookup"><span data-stu-id="81068-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="81068-128">Les problèmes sont signalés sous forme d’avertissements dans la fenêtre Liste d’erreurs de Visual Studio, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="81068-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problèmes signalés par l’analyseur d’infrastructure](./media/framework-analyzers-2.png)

<span data-ttu-id="81068-130">Au fil de l’écriture du code, vous voyez des marques ondulées sous les problèmes potentiels de votre code.</span><span class="sxs-lookup"><span data-stu-id="81068-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="81068-131">Placez le curseur sur un problème pour voir plus d’informations sur celui-ci, ainsi que des suggestions pour une correction possible, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="81068-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![rapport interactif des problèmes détectés par l’Analyseur de framework](./media/framework-analyzers-1.png)

<span data-ttu-id="81068-133">Les analyseurs examinent le code de votre solution et vous fournissent une liste d’avertissements pour ces problèmes :</span><span class="sxs-lookup"><span data-stu-id="81068-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="81068-134">CA1058 : Les types ne doivent pas étendre certains types de base</span><span class="sxs-lookup"><span data-stu-id="81068-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="81068-135">Vous ne devez rien dériver directement d’un petit nombre de types du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81068-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span>

<span data-ttu-id="81068-136">**Catégorie :** Conception</span><span class="sxs-lookup"><span data-stu-id="81068-136">**Category:** Design</span></span>

<span data-ttu-id="81068-137">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-137">**Severity:** Warning</span></span>

<span data-ttu-id="81068-138">Informations supplémentaires : [CA1058 : Les types ne doivent pas étendre certains types de base](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="81068-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="81068-139">CA2153 : Ne pas intercepter des exceptions d’état endommagé</span><span class="sxs-lookup"><span data-stu-id="81068-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="81068-140">L’interception des exceptions d’état endommagé pourrait masquer des erreurs (comme des violations d’accès), aboutissant à un état d’exécution incohérent ou facilitant la compromission d’un système par des attaquants.</span><span class="sxs-lookup"><span data-stu-id="81068-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="81068-141">Au lieu de cela, il faut intercepter et gérer un ensemble de types d’exception plus spécifiques, ou lever à nouveau l’exception.</span><span class="sxs-lookup"><span data-stu-id="81068-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="81068-142">**Catégorie :** Sécurité</span><span class="sxs-lookup"><span data-stu-id="81068-142">**Category:** Security</span></span>

<span data-ttu-id="81068-143">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-143">**Severity:** Warning</span></span>

<span data-ttu-id="81068-144">Informations supplémentaires : [## CA2153 : Ne pas intercepter les exceptions d’état endommagé](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="81068-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="81068-145">CA2229 : Implémentez des constructeurs de sérialisation</span><span class="sxs-lookup"><span data-stu-id="81068-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="81068-146">L’analyseur génère cet avertissement quand vous créez un type qui implémente l’interface <xref:System.Runtime.Serialization.ISerializable>, mais ne définit pas le constructeur de sérialisation nécessaire.</span><span class="sxs-lookup"><span data-stu-id="81068-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="81068-147">Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="81068-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="81068-148">Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.</span><span class="sxs-lookup"><span data-stu-id="81068-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="81068-149">Le constructeur de sérialisation a la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="81068-149">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="81068-150">**Catégorie :** Utilisation</span><span class="sxs-lookup"><span data-stu-id="81068-150">**Category:** Usage</span></span>

<span data-ttu-id="81068-151">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-151">**Severity:** Warning</span></span>

<span data-ttu-id="81068-152">Informations supplémentaires : [CA2229 : Implémentez des constructeurs de sérialisation](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="81068-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="81068-153">CA2235 : Marquez tous les champs non sérialisés</span><span class="sxs-lookup"><span data-stu-id="81068-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="81068-154">Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.</span><span class="sxs-lookup"><span data-stu-id="81068-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="81068-155">Vous devez marquer explicitement ce champ avec <xref:System.NonSerializedAttribute> pour résoudre cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="81068-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="81068-156">**Catégorie :** Utilisation</span><span class="sxs-lookup"><span data-stu-id="81068-156">**Category:** Usage</span></span>

<span data-ttu-id="81068-157">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-157">**Severity:** Warning</span></span>

<span data-ttu-id="81068-158">Informations supplémentaires : [CA2235 : Marquez tous les champs non sérialisables](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="81068-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="81068-159">CA2237 : Marquez les types ISerializable comme étant sérialisables</span><span class="sxs-lookup"><span data-stu-id="81068-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="81068-160">Pour être reconnus par le Common Language Runtime comme étant sérialisables, les types doivent être marqués avec l’attribut <xref:System.SerializableAttribute>, même s’ils utilisent une routine de sérialisation personnalisée en implémentant l’interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="81068-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="81068-161">**Catégorie :** Utilisation</span><span class="sxs-lookup"><span data-stu-id="81068-161">**Category:** Usage</span></span>

<span data-ttu-id="81068-162">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-162">**Severity:** Warning</span></span>

<span data-ttu-id="81068-163">Informations supplémentaires : [CA2237 : Marquez les types ISerializable comme étant sérialisables](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="81068-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="81068-164">CA3075 : Traitement du DTD non sécurisé dans XML</span><span class="sxs-lookup"><span data-stu-id="81068-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="81068-165">Si vous utilisez des instances de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> non sécurisées ou référencez des sources d’entités externes, l’analyseur peut accepter une entrée non fiable et divulguer des informations sensibles à des personnes malveillantes.</span><span class="sxs-lookup"><span data-stu-id="81068-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="81068-166">**Catégorie :** Sécurité</span><span class="sxs-lookup"><span data-stu-id="81068-166">**Category:** Security</span></span>

<span data-ttu-id="81068-167">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-167">**Severity:** Warning</span></span>

<span data-ttu-id="81068-168">Informations supplémentaires : [A3075 : Traitement du DTD non sécurisé dans XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="81068-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="81068-169">CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles</span><span class="sxs-lookup"><span data-stu-id="81068-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="81068-170">Les algorithmes de chiffrement se dégradent au fil du temps, car les attaques deviennent plus sophistiquées.</span><span class="sxs-lookup"><span data-stu-id="81068-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="81068-171">Selon le type et l’application de cet algorithme de chiffrement, une dégradation progressive de sa force de chiffrement peut permettre aux attaquants de lire des messages chiffrés, de falsifier des messages chiffrés, de falsifier des signatures numériques, de falsifier du contenu haché ou de compromettre les systèmes de chiffrement basés sur cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="81068-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="81068-172">Pour le chiffrement, utilisez un algorithme AES (AES-256, AES-192 et AES-128 sont acceptables) avec une longueur de clé supérieure ou égale à 128 bits.</span><span class="sxs-lookup"><span data-stu-id="81068-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="81068-173">Pour le hachage, utilisez une fonction de hachage de la famille SHA-2, comme SHA-2 512, SHA-2 384 ou SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="81068-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="81068-174">**Catégorie :** Sécurité</span><span class="sxs-lookup"><span data-stu-id="81068-174">**Category:** Security</span></span>

<span data-ttu-id="81068-175">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-175">**Severity:** Warning</span></span>

<span data-ttu-id="81068-176">Informations supplémentaires : [CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="81068-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="81068-177">CA5351 : N’utilisez pas les algorithmes de chiffrement cassés</span><span class="sxs-lookup"><span data-stu-id="81068-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="81068-178">Il existe une attaque qui permet de casser cet algorithme par voie informatique.</span><span class="sxs-lookup"><span data-stu-id="81068-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="81068-179">Ceci permet aux attaquants de passer outre les garanties en matière de chiffrement qu’il doit normalement fournir.</span><span class="sxs-lookup"><span data-stu-id="81068-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="81068-180">Selon le type et l’application de cet algorithme de chiffrement, ceci peut permettre aux attaquants de lire des messages chiffrés, de falsifier des messages chiffrés, de falsifier des signatures numériques, de falsifier du contenu haché ou de compromettre les systèmes de chiffrement basés sur cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="81068-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="81068-181">Pour le chiffrement, utilisez un algorithme AES (AES-256, AES-192 et AES-128 sont acceptables) avec une longueur de clé supérieure ou égale à 128 bits.</span><span class="sxs-lookup"><span data-stu-id="81068-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="81068-182">Pour le hachage, utilisez une fonction de hachage de la famille SHA-2, comme SHA512, SHA384 ou SHA256.</span><span class="sxs-lookup"><span data-stu-id="81068-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="81068-183">Pour les signatures numériques, utilisez RSA avec une longueur de clé supérieure ou égale à 2048 bits, ou ECDSA avec une longueur de clé supérieure ou égale à 256 bits.</span><span class="sxs-lookup"><span data-stu-id="81068-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="81068-184">**Catégorie :** Sécurité</span><span class="sxs-lookup"><span data-stu-id="81068-184">**Category:** Security</span></span>

<span data-ttu-id="81068-185">**Sévérité:** Avertissement</span><span class="sxs-lookup"><span data-stu-id="81068-185">**Severity:** Warning</span></span>

<span data-ttu-id="81068-186">Informations supplémentaires : [CA5351 : N’utilisez pas d’algorithmes de chiffrement cassés](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="81068-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
